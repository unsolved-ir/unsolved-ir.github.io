# unsolved-ir.github.io

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Unsolved — Open IR Research Questions Not Solved by LLMs | Berlin, March 2027</title>
<meta name="description" content="A student-written research agenda for information retrieval. A SIGIR Futures activity, collocated with ACM SIGIR CHIIR 2027.">
<meta property="og:title" content="Unsolved — Open IR Research Questions Not Solved by LLMs">
<meta property="og:description" content="PhD students are writing the next IR research agenda. Berlin, March 2027.">
<meta property="og:type" content="website">
<!-- TODO: og:url and og:image once the domain exists -->

<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Archivo:wght@400;500;600;700&family=Newsreader:ital,opsz,wght@0,6..72,400;0,6..72,500;1,6..72,400&display=swap" rel="stylesheet">

<style>
/* ===========================================================
   UNSOLVED — CHIIR 2027 satellite
   Red marks three things only: the caret, deadlines, and the
   one required field. Never decoration.
   Yellow = something you still have to write. Delete the
   .todo rule at the bottom when the page is finished.
   =========================================================== */

:root{
  color-scheme: light;
  --paper:     #E3E1DB;
  --paper-alt: #D9D6CE;
  --ink:       #000000;
  --soft:      #46443E;
  --rule:      #B7B3A9;
  --mark:      #B3221F;
  --sans: "Archivo","Helvetica Neue",Helvetica,Arial,sans-serif;
  --serif: "Newsreader",Georgia,"Times New Roman",serif;
  --gutter: clamp(1.25rem,5vw,5rem);
}
*,*::before,*::after{ box-sizing:border-box; }
html{ -webkit-text-size-adjust:100%; scroll-behavior:smooth; }
@media (prefers-reduced-motion: reduce){ html{ scroll-behavior:auto; } }

body{
  margin:0; background:var(--paper); color:var(--ink);
  font-family:var(--serif); font-size:clamp(1rem,.96rem + .2vw,1.0625rem);
  line-height:1.6; font-synthesis-weight:none;
}

.wrap{ max-width:1180px; margin:0 auto; padding-inline:var(--gutter); }
.band{ padding-block:clamp(3rem,7vw,5.5rem); border-top:1px solid var(--rule); }
.band--alt{ background:var(--paper-alt); }
.band--invert{ background:var(--ink); color:var(--paper); border-top:0; }

h1,h2,h3{ font-family:var(--sans); font-weight:600; margin:0; text-wrap:balance; }
h2{ font-size:clamp(1.6rem,1.1rem + 2.3vw,2.6rem); letter-spacing:-.025em; line-height:1.05; margin-bottom:1.25rem; }
h3{ font-size:clamp(1rem,.97rem + .3vw,1.13rem); letter-spacing:-.008em; margin-bottom:.3rem; }
p{ margin:0 0 .9em; max-width:60ch; }
p:last-child{ margin-bottom:0; }
.lede{ font-size:clamp(1.05rem,1rem + .55vw,1.3rem); line-height:1.45; color:var(--soft); max-width:50ch; }
.band--invert .lede{ color:#C9C6BE; }

a{ color:inherit; text-underline-offset:.18em; text-decoration-thickness:1px; text-decoration-color:var(--rule); }
a:hover{ text-decoration-color:var(--mark); }
:focus-visible{ outline:2px solid var(--mark); outline-offset:3px; }
.skip{ position:absolute; left:-9999px; background:var(--ink); color:var(--paper); padding:.7rem 1rem; font-family:var(--sans); z-index:100; }
.skip:focus{ left:0; }

/* ---- nav ---- */
.nav{ position:sticky; top:0; z-index:50; background:rgba(227,225,219,.93); backdrop-filter:blur(8px); border-bottom:1px solid var(--rule); }
.nav__inner{ max-width:1180px; margin:0 auto; padding:.7rem var(--gutter); display:flex; align-items:baseline; gap:1.5rem; flex-wrap:wrap; }
.nav__mark{ font-family:var(--sans); font-weight:700; letter-spacing:-.03em; font-size:1.05rem; text-decoration:none; }
.nav__links{ display:flex; gap:1.15rem; flex-wrap:wrap; margin-left:auto; font-family:var(--sans); font-size:.88rem; font-weight:500; }
.nav__links a{ text-decoration:none; color:var(--soft); }
.nav__links a:hover{ color:var(--ink); }
@media (max-width:720px){
  .nav__inner{ flex-wrap:nowrap; align-items:center; gap:.85rem; }
  .nav__links{ flex-wrap:nowrap; overflow-x:auto; gap:1rem; scrollbar-width:none; -ms-overflow-style:none;
    mask-image:linear-gradient(to right,#000 88%,transparent); }
  .nav__links::-webkit-scrollbar{ display:none; }
  .nav__links a{ white-space:nowrap; }
}

/* ---- the search box: the one loud thing ---- */
.hero{ padding-block:clamp(2.5rem,7vw,5rem) clamp(2rem,5vw,3.5rem); }

.search{
  max-width:33rem; border:2px solid var(--ink); background:var(--paper);
  padding:clamp(.8rem,2vw,1.05rem) clamp(.9rem,2.2vw,1.2rem);
  display:flex; align-items:center; gap:.7rem;
}
.search svg{ flex:none; width:1.15rem; height:1.15rem; }
.search__q{
  font-family:var(--serif); font-size:clamp(1.05rem,.95rem + .7vw,1.45rem);
  line-height:1.2; white-space:nowrap; overflow:hidden;
}
.caret{
  display:inline-block; width:.5ch; height:1.05em; background:var(--mark);
  vertical-align:-.14em; margin-left:.06em;
}
@media (prefers-reduced-motion: no-preference){
  .caret{ animation:blink 1.05s steps(1) infinite; }
  @keyframes blink{ 50%{ opacity:0; } }
}
.search__res{
  font-family:var(--sans); font-size:.85rem; font-weight:500; color:var(--mark);
  margin:.6rem 0 0; height:1.2em; opacity:0; transition:opacity .4s ease;
}
.search__res.is-in{ opacity:1; }

.hero__mark{ font-family:var(--sans); font-weight:700; font-size:clamp(3.5rem,15vw,12rem);
  line-height:.86; letter-spacing:-.055em; margin:clamp(1.75rem,4vw,2.75rem) 0 clamp(1rem,2.5vw,1.6rem); }
.hero__title{ font-family:var(--serif); font-weight:400; font-size:clamp(1.15rem,1rem + 1.2vw,1.75rem);
  line-height:1.3; max-width:26ch; margin:0 0 1.4rem; }
.hero__where{ font-family:var(--sans); font-weight:500; font-size:.98rem; line-height:1.5;
  color:var(--soft); max-width:42ch; margin:0 0 2rem; }
.hero__where strong{ color:var(--ink); font-weight:600; }

/* ---- buttons ---- */
.actions{ display:flex; flex-wrap:wrap; gap:.7rem; }
.btn{ font-family:var(--sans); font-weight:600; font-size:.95rem; padding:.72rem 1.25rem;
  border-radius:2px; border:1px solid var(--ink); text-decoration:none; display:inline-block; line-height:1.2; }
.btn--solid{ background:var(--ink); color:var(--paper); }
.btn--solid:hover{ background:var(--mark); border-color:var(--mark); }
.btn--ghost{ background:transparent; color:var(--ink); }
.btn--ghost:hover{ background:var(--ink); color:var(--paper); }
.band--invert .btn--solid{ background:var(--paper); color:var(--ink); border-color:var(--paper); }
.band--invert .btn--solid:hover{ background:transparent; color:var(--paper); }

/* ---- question list (supporting, not a hero) ---- */
.qlist{ list-style:none; margin:0; padding:0; }
.qlist li{ font-family:var(--serif); font-size:clamp(1.15rem,1rem + .85vw,1.55rem); line-height:1.22;
  padding-bottom:.65rem; margin-bottom:.65rem; border-bottom:2px solid var(--mark); max-width:26ch; }
@media (min-width:820px){ .qlist{ columns:2; column-gap:clamp(2rem,5vw,4rem); } .qlist li{ break-inside:avoid; } }

/* ---- two-column ---- */
.cols{ display:grid; gap:clamp(1.5rem,4vw,3rem); }
@media (min-width:900px){ .cols--aside{ grid-template-columns:minmax(0,1fr) minmax(0,.68fr); align-items:start; } }
.aside{ font-size:.93rem; line-height:1.55; color:var(--soft); border-top:2px solid var(--ink); padding-top:.8rem; max-width:38ch; }

/* ---- phases ---- */
.phases{ list-style:none; margin:0; padding:0; counter-reset:phase; }
.phases > li{ counter-increment:phase; border-top:1px solid var(--rule); padding:1.2rem 0; display:grid; gap:.25rem 1.5rem; }
.phases > li:last-child{ border-bottom:1px solid var(--rule); }
@media (min-width:760px){ .phases > li{ grid-template-columns:3.25rem minmax(0,1fr); } .phases > li::before{ grid-row:1 / span 3; } }
.phases > li::before{ content:counter(phase); font-family:var(--sans); font-weight:700; font-size:1.3rem; line-height:1.1; letter-spacing:-.03em; color:var(--mark); }
.phases p{ margin:0; max-width:58ch; font-size:.98rem; }
.when{ font-family:var(--sans); font-size:.84rem; font-weight:500; color:var(--soft); margin-top:.35rem; }

/* ---- template fields ---- */
.fields{ margin:0; border-top:2px solid var(--ink); }
.fields > div{ display:grid; gap:.1rem 1.5rem; padding:.8rem 0; border-bottom:1px solid var(--rule); }
@media (min-width:760px){ .fields > div{ grid-template-columns:minmax(0,15rem) minmax(0,1fr) 7rem; align-items:baseline; } }
.fields dt{ font-family:var(--sans); font-weight:600; font-size:.96rem; }
.fields dd{ margin:0; color:var(--soft); font-size:.93rem; line-height:1.45; }
.fields .limit{ font-family:var(--sans); font-size:.84rem; color:var(--soft); }
@media (min-width:760px){ .fields .limit{ text-align:right; } }
.fields .key{ color:var(--mark); }

/* ---- topics ---- */
.topics{ display:grid; gap:clamp(1.5rem,4vw,2.5rem); }
@media (min-width:780px){ .topics{ grid-template-columns:repeat(3,minmax(0,1fr)); } }
.topics h3{ border-top:2px solid var(--ink); padding-top:.7rem; margin-bottom:.6rem; }
.topics ul{ margin:0; padding:0; list-style:none; }
.topics li{ font-size:.93rem; line-height:1.4; color:var(--soft); padding:.45rem 0; border-top:1px solid var(--rule); }
.topics li:first-child{ border-top:0; padding-top:0; }

/* ---- dates ---- */
.dates{ margin:0; border-top:2px solid var(--ink); max-width:44rem; }
.dates > div{ display:flex; flex-wrap:wrap; gap:.2rem 1.5rem; justify-content:space-between; padding:.7rem 0; border-bottom:1px solid var(--rule); }
.dates dt{ font-family:var(--sans); font-weight:500; font-size:.94rem; flex:1 1 17rem; }
.dates dd{ margin:0; font-family:var(--sans); font-weight:600; font-size:.94rem; white-space:nowrap; }
.dates .is-deadline dd{ color:var(--mark); }
.dates .is-event{ border-bottom:2px solid var(--ink); }
.dates .is-event dt,.dates .is-event dd{ font-weight:700; font-size:1.02rem; }

.note{ font-size:.9rem; color:var(--soft); margin-top:1rem; max-width:50ch; line-height:1.5; }

/* ---- faq ---- */
.faq{ border-top:2px solid var(--ink); max-width:54rem; }
.faq details{ border-bottom:1px solid var(--rule); }
.faq summary{ font-family:var(--sans); font-weight:600; font-size:.98rem; padding:.9rem 2rem .9rem 0; cursor:pointer; list-style:none; position:relative; }
.faq summary::-webkit-details-marker{ display:none; }
.faq summary::after{ content:"+"; position:absolute; right:.25rem; top:.85rem; font-family:var(--sans); font-size:1.2rem; color:var(--mark); }
.faq details[open] summary::after{ content:"\2013"; }
.faq details p{ font-size:.96rem; margin-bottom:.9rem; }

/* ---- people ---- */
.people{ display:grid; gap:1.2rem 2.5rem; margin-top:1.25rem; }
@media (min-width:700px){ .people{ grid-template-columns:repeat(2,minmax(0,1fr)); } }
.people > div{ border-top:1px solid var(--rule); padding-top:.75rem; }
.people h3{ font-size:.98rem; margin-bottom:.15rem; }
.people p{ font-size:.91rem; color:var(--soft); margin:0; }

/* ---- footer ---- */
.foot{ border-top:1px solid var(--rule); padding-block:2.25rem 3rem; font-family:var(--sans); font-size:.85rem; color:var(--soft); }
.foot p{ max-width:58ch; margin-bottom:.5rem; }

/* ---- placeholders: delete this rule when the page is done ---- */
.todo{ background:#F7E6A6; color:#000; box-shadow:0 0 0 2px #F7E6A6; border-radius:1px; }
</style>
</head>

<body>
<a class="skip" href="#main">Skip to content</a>

<nav class="nav" aria-label="Sections">
  <div class="nav__inner">
    <a class="nav__mark" href="#top">Unsolved</a>
    <div class="nav__links">
      <a href="#call">The call</a>
      <a href="#how">How it works</a>
      <a href="#submit">What to write</a>
      <a href="#support">Funding</a>
      <a href="#dates">Dates</a>
      <a href="#faq">FAQ</a>
      <a href="#contact">Contact</a>
    </div>
  </div>
</nav>

<main id="main">

<!-- ================= HERO ================= -->
<section id="top" class="hero">
  <div class="wrap">

    <div class="search" role="img" aria-label="A search box containing the query: has it all been solved? Zero results.">
      <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" aria-hidden="true">
        <circle cx="10.5" cy="10.5" r="6.5"/><path d="M15.5 15.5 L21 21"/>
      </svg>
      <span class="search__q"><span id="q"></span><span class="caret" aria-hidden="true"></span></span>
    </div>
    <p class="search__res" id="qres">0 results.</p>

    <h1 class="hero__mark">Unsolved</h1>
    <p class="hero__title">Defining a new IR playground: open information retrieval research questions not solved by LLMs.</p>
    <p class="hero__where">
      <strong>Berlin, March 2027.</strong><br>
      A SIGIR Futures activity, collocated with ACM SIGIR CHIIR 2027.
    </p>

    <div class="actions">
      <a class="btn btn--solid" href="REPLACE-WITH-SUBMISSION-FORM-URL">Submit a research direction</a>
      <a class="btn btn--ghost" href="REPLACE-WITH-PC-SIGNUP-URL">Join the program committee</a>
      <a class="btn btn--ghost" href="REPLACE-WITH-MAILING-LIST-URL">Get updates</a>
    </div>

  </div>
</section>

<!-- ================= QUESTIONS =================
     Swap these for the best ones that arrive in submissions.
     Keep it at four. The point is that it stops. -->
<section class="band">
  <div class="wrap">
    <ul class="qlist">
      <li>If there is no ranked list, what is relevance?</li>
      <li>How do you build a test collection the next model has not read?</li>
      <li>What do you measure when the task was “help me understand”?</li>
      <li class="todo">[Replace with a fourth question — ideally user-centered]</li>
    </ul>
  </div>
</section>

<!-- ================= THE CALL ================= -->
<section id="call" class="band band--alt">
  <div class="wrap cols cols--aside">
    <div>
      <h2>The people who will do the work have not been asked what the work is</h2>
      <p>Research agendas for IR get written every few years by people mostly past the point of writing theses. Unsolved is the other half of that conversation: PhD students and early-career researchers writing the agenda together, over five months, ending in Berlin.</p>
      <p class="todo">[One paragraph, ~70 words: what the document will actually contain, and why "not solved by LLMs" is the filter rather than "about LLMs". Jaap's phrasing from the proposal is a good starting point.]</p>
      <p class="todo">[One short paragraph: not a call for papers, nothing is rejected, the competition is only over who does the most to make it good. Jaap calls this a coopetition — decide whether that word goes on the public site.]</p>
    </div>
    <div class="aside">
      <h3>Precedent, from NLP</h3>
      <p><a href="https://aclanthology.org/2023.findings-emnlp.799/">Defining a New NLP Playground</a> (EMNLP Findings 2023) and <a href="https://aclanthology.org/2024.lrec-main.708/">Has It All Been Solved?</a> (LREC-COLING 2024).</p>
      <p class="todo">[Two sentences: why those two are useful, and that IR has no equivalent. Do not claim the second was a student rebuttal to the first — check the arXiv dates.]</p>
    </div>
  </div>
</section>

<!-- ================= HOW IT WORKS ================= -->
<section id="how" class="band">
  <div class="wrap">
    <h2>How it works</h2>
    <p class="lede">Most of the work happens before and after Berlin. You do not need to be in the room.</p>

    <ol class="phases">
      <li>
        <h3>Write one research direction</h3>
        <p>500 to 800 words, fixed template. Open to everyone. PC members submit too.</p>
        <p class="when">Deadline <span class="todo">11 January 2027</span>, earlier track for visas</p>
      </li>
      <li>
        <h3>Review in both directions</h3>
        <p>The PC comments on every submission, then the submitters comment on the PC's directions. Nothing is rejected.</p>
        <p class="when"><span class="todo">12–25 January 2027</span></p>
      </li>
      <li>
        <h3>Areas, and student leads</h3>
        <p>Directions grouped into areas of three to five. From here the students run it.</p>
        <p class="when">Announced <span class="todo">27 January 2027</span></p>
      </li>
      <li>
        <h3>Berlin</h3>
        <p class="todo">[One line on the day itself. Draft: leads present, breakouts sharpen, every area reports its top three. Confirm the format with Jaap first.]</p>
        <p class="when"><span class="todo">March 2027, day to be confirmed</span></p>
      </li>
      <li>
        <h3>The agenda</h3>
        <p>SIGIR Forum, December 2027. Perspective papers to SIGIR 2028. Contributors are named authors whether or not they were in Berlin.</p>
      </li>
    </ol>
  </div>
</section>

<!-- ================= WHAT TO WRITE ================= -->
<section id="submit" class="band band--alt">
  <div class="wrap">
    <h2>What to write</h2>
    <p class="lede">One direction per submission. The template is fixed so that forty of them can be merged into one document.</p>

    <dl class="fields">
      <div><dt>Title of the direction</dt><dd>The problem, not the method.</dd><dd class="limit">12 words</dd></div>
      <div><dt>The question</dt><dd>If it takes two sentences, it is two directions.</dd><dd class="limit">1 sentence</dd></div>
      <div><dt>Why it matters</dt><dd>Who is worse off while it stays open.</dd><dd class="limit">150 words</dd></div>
      <div><dt class="key">Why LLMs do not solve it, and why the next generation will not either</dt><dd>The load-bearing field.</dd><dd class="limit">200 words</dd></div>
      <div><dt>What a first study looks like</dt><dd>Startable in six months, on a normal budget.</dd><dd class="limit">150 words</dd></div>
      <div><dt>How we would know we made progress</dt><dd>What would count as evidence.</dd><dd class="limit">100 words</dd></div>
      <div><dt>Related work</dt><dd>Enough to show it is open.</dd><dd class="limit">5 refs</dd></div>
      <div><dt>About you</dt><dd>Affiliation, career stage, and whether you already have funding to attend.</dd><dd class="limit">—</dd></div>
      <div><dt>LLM use</dt><dd>Allowed. Disclose it.</dd><dd class="limit">—</dd></div>
    </dl>

    <p class="note todo">[Decide and state: can you submit more than one? Draft answer — yes, but only one counts toward area and funding allocation.]</p>
  </div>
</section>

<!-- ================= FUNDING ================= -->
<section id="support" class="band band--invert">
  <div class="wrap cols cols--aside">
    <div>
      <h2>We will pay for some of you to be there</h2>
      <p class="lede">ACM SIGIR, through its Futures initiative, has committed 10,000 USD. Most of it becomes CHIIR 2027 registration waivers.</p>
      <p>Each area gets one or more waivers and decides among itself who receives them, weighing contribution and need, by <span class="todo">8 February 2027</span>.</p>
      <p class="todo">[The tie-break rule. Draft: an unclaimed waiver returns to the pool and goes to another area. Jaap's original wording was "nobody gets it". Pick one, get his sign-off, publish it before submissions open.]</p>
      <p class="todo">[Two lines on travel support beyond a waiver, and who it prioritises. Confirm the ACM reimbursement route with Maria first — whether students have to front the money changes what you can promise here.]</p>
      <p>Waivers go to student members. Organizers and their own students are not eligible.</p>
    </div>
    <div class="aside" style="border-color:var(--paper); color:#C9C6BE">
      <h3 style="color:var(--paper)">Why it is allocated this way</h3>
      <p class="todo" style="box-shadow:none">[~50 words: funding by paper acceptance funds students who already had a travel budget; this funds contribution to a shared document instead, then trusts the people closest to the situation to judge need.]</p>
    </div>
  </div>
</section>

<!-- ================= TOPICS ================= -->
<section id="topics" class="band">
  <div class="wrap">
    <h2>Things you might write about</h2>
    <p class="lede">Prompts, not categories. Areas are formed from what arrives.</p>
    <div class="topics">
      <div>
        <h3>Systems, evaluation, resources</h3>
        <ul>
          <li>Evaluation when the system is generative and non-deterministic</li>
          <li>Test collections the next model has not already read</li>
          <li>Reproducibility against a model target that moves every quarter</li>
          <li>Cost, latency and energy as first-class retrieval metrics</li>
          <li class="todo">[Add 3–4 more]</li>
        </ul>
      </div>
      <div>
        <h3>People and interaction</h3>
        <ul>
          <li>Measuring learning and sensemaking, not task completion</li>
          <li>Over-reliance, and whether users can detect a wrong answer</li>
          <li>Agentic search: delegation, oversight, repair</li>
          <li>Simulated users, and where the substitution breaks</li>
          <li class="todo">[Add 3–4 more]</li>
        </ul>
      </div>
      <div>
        <h3>The field itself</h3>
        <ul>
          <li>Provenance, and the economics of sources summarized away</li>
          <li>Who the models were not built for</li>
          <li>Synthetic participants and research ethics</li>
          <li>What happens to a field whose benchmarks are saturated</li>
          <li class="todo">[Add 3–4 more]</li>
        </ul>
      </div>
    </div>
  </div>
</section>

<!-- ================= DATES ================= -->
<section id="dates" class="band band--alt">
  <div class="wrap">
    <h2>Dates</h2>
    <dl class="dates">
      <div><dt>Call opens</dt><dd class="todo">Late October 2026</dd></div>
      <div><dt>PC sign-up closes</dt><dd class="todo">13 November 2026</dd></div>
      <div class="is-deadline"><dt>Early deadline, for anyone needing a visa</dt><dd class="todo">16 November 2026</dd></div>
      <div><dt>Early notifications and invitation letters</dt><dd class="todo">30 November 2026</dd></div>
      <div class="is-deadline"><dt>Main submission deadline</dt><dd class="todo">11 January 2027</dd></div>
      <div><dt>Reciprocal review round</dt><dd class="todo">12–25 January 2027</dd></div>
      <div><dt>Areas announced, waivers allocated</dt><dd class="todo">27 January 2027</dd></div>
      <div class="is-deadline"><dt>Areas report waiver decisions</dt><dd class="todo">8 February 2027</dd></div>
      <div><dt>First drafts from each area</dt><dd class="todo">22 February 2027</dd></div>
      <div class="is-event"><dt>Unsolved, in Berlin</dt><dd class="todo">March 2027</dd></div>
      <div><dt>Report in SIGIR Forum</dt><dd>December 2027</dd></div>
      <div><dt>Perspective papers</dt><dd>SIGIR 2028</dd></div>
    </dl>
    <p class="note">CHIIR 2027 runs 7–11 March 2027 at Humboldt-Universität zu Berlin. All deadlines 23:59 anywhere on earth.</p>
    <p class="note todo">[Check every date above against the CHIIR registration calendar. The one that matters: waiver notification must land before early-bird closes.]</p>
  </div>
</section>

<!-- ================= FAQ ================= -->
<section id="faq" class="band">
  <div class="wrap">
    <h2>Questions people have asked</h2>
    <div class="faq">
      <details>
        <summary>Do I have to be a PhD student?</summary>
        <p>No. Anyone can write a direction. The waivers are for student members, and the areas are led by students.</p>
      </details>
      <details>
        <summary>Do I have to come to Berlin?</summary>
        <p>No. Contributors who cannot travel are authors on the same terms.</p>
      </details>
      <details>
        <summary>Can my submission be rejected?</summary>
        <p>No. Revision requests, not rejections.</p>
      </details>
      <details>
        <summary>Does this count as a publication?</summary>
        <p class="todo">[Draft: submissions non-archival, published on this site under CC BY with consent, becoming a SIGIR Forum report in December 2027 and perspective papers at SIGIR 2028. Confirm the licence with Jaap.]</p>
      </details>
      <details>
        <summary>How is authorship decided?</summary>
        <p class="todo">[Draft: an included direction plus one writing round equals named authorship, alphabetical order, go quiet and you move to acknowledgments. Agree this with Jaap before it goes public — it is the thing most likely to cause trouble later.]</p>
      </details>
      <details>
        <summary>How much work is this?</summary>
        <p class="todo">[Draft: half a day to write, a couple of hours reviewing, then whatever your area decides between January and March.]</p>
      </details>
      <details>
        <summary>Can I use an LLM to write my submission?</summary>
        <p>Yes, and say so. The ideas have to be yours.</p>
      </details>
      <details>
        <summary>I need a visa for Germany.</summary>
        <p>Use the early deadline, <span class="todo">16 November 2026</span>. Invitation letters go out <span class="todo">30 November</span>. Appointment waits in some countries are longer than the time that leaves, so do not wait for the main deadline.</p>
      </details>
      <details>
        <summary>Can I help organize it?</summary>
        <p>Yes. Areas, publicity, the website, editing the report. <a href="REPLACE-WITH-CONTACT-EMAIL-LINK">Write to us</a>.</p>
      </details>
    </div>
  </div>
</section>

<!-- ================= CONTACT ================= -->
<section id="contact" class="band band--alt">
  <div class="wrap">
    <h2>Who is doing this</h2>
    <p class="lede">A SIGIR Futures activity, run by students as far as we can push it.</p>

    <div class="people">
      <div>
        <h3>Jaap Kamps</h3>
        <p>University of Amsterdam. Coordinator.</p>
      </div>
      <div>
        <h3 class="todo">[Your name]</h3>
        <p class="todo">[University of Amsterdam. Chair.]</p>
      </div>
      <div>
        <h3 class="todo">[Local chair]</h3>
        <p class="todo">[Humboldt-Universität zu Berlin.]</p>
      </div>
      <div>
        <h3 class="todo">[More names]</h3>
        <p class="todo">[Publicity, web, areas, editing. The Berlin, Regensburg and Amsterdam students who were at CHIIR 2026.]</p>
      </div>
    </div>

    <div class="actions" style="margin-top:2rem">
      <a class="btn btn--solid" href="REPLACE-WITH-SUBMISSION-FORM-URL">Submit a research direction</a>
      <a class="btn btn--ghost" href="REPLACE-WITH-PC-SIGNUP-URL">Join the program committee</a>
    </div>
  </div>
</section>

</main>

<footer class="foot">
  <div class="wrap">
    <p>A SIGIR Futures activity, collocated with ACM SIGIR CHIIR 2027, Humboldt-Universität zu Berlin, 7–11 March 2027. Organized independently of the CHIIR 2027 program committee.</p>
    <p>Contact <a href="REPLACE-WITH-CONTACT-EMAIL-LINK">REPLACE-WITH-CONTACT-EMAIL</a>.</p>
    <p class="todo">[Privacy notice. Needs a named data controller (UvA or HU Berlin), what you collect, how long you keep it, and how to ask for removal. Not optional — you are collecting names, emails and funding status in Germany.]</p>
  </div>
</footer>

<script>
(function () {
  var el = document.getElementById('q');
  var res = document.getElementById('qres');
  var text = 'has it all been solved?';   // <- change the query here
  var reduce = window.matchMedia('(prefers-reduced-motion: reduce)').matches;

  if (reduce) { el.textContent = text; res.classList.add('is-in'); return; }

  var i = 0;
  function tick() {
    el.textContent = text.slice(0, ++i);
    if (i < text.length) setTimeout(tick, 52 + Math.random() * 48);
    else setTimeout(function () { res.classList.add('is-in'); }, 600);
  }
  setTimeout(tick, 450);
})();
</script>

</body>
</html>
