# Theory of Computation and the Foundations of Computing

*8-Week Program with Weekly Common Lisp Practicals, for Advanced Undergraduate and Early Graduate Students*

## Program Information

- **Duration:** 8 weeks
- **Suggested load:** 10 to 12 hours per week (about 3 h primary reading, 2 h textbook, 1 h lectures, 4 h practical, 1 h reflection)
- **Learning mode:** independent. Each learner reads, watches, codes and reflects on their own during the week.
- **Weekly meeting:** every Saturday, 4:00 to 5:00 pm, run by that week's lead (Yacouba to Diallo & Seb for Weeks 1 to 8). See "Weekly Meeting and Week Leads" below.
- **Prerequisites:** discrete mathematics (sets, functions, relations, proof by induction and contradiction) and some programming experience. No Lisp is assumed; Week 1 sets up the tools.
- **Language and tools:** GNU CLISP, an ANSI Common Lisp implementation, used entirely from the terminal: the `clisp` REPL, `clisp file.lisp` to run scripts, and any plain text editor (vim, nano, micro or similar). No IDE, SLIME or external libraries are required.
- **Repository:** a GitHub account and one personal repository are required; the repository name and organisation are to be decided. All weekly work is committed and pushed there (see below).
- **Lisp references:** Graham, *ANSI Common Lisp* (Prentice Hall, 1996) and Norvig, *Paradigms of Artificial Intelligence Programming* (PAIP, Morgan Kaufmann, 1992), online at [norvig.com/paip.html](https://norvig.com/paip.html) with text and code also at [github.com/norvig/paip-lisp](https://github.com/norvig/paip-lisp).

## Course Description

This program teaches the theory of computation through the papers that created it. Learners move from finite automata and formal grammars to Turing's 1936 paper *On Computable Numbers, with an Application to the Entscheidungsproblem*, then to Church's lambda calculus, McCarthy's 1960 paper that introduced Lisp, and finally to computational complexity. Each week pairs a primary source and a textbook chapter with a practical in Common Lisp. Lisp is a good fit because programs are ordinary data (s-expressions), which makes encodings, interpreters, diagonal arguments and reductions concrete: you build the objects the theorems talk about, and then run them.

## Learning Outcomes

By the end of the program, learners will be able to:

1. Explain the Entscheidungsproblem and why Turing and Church's answers changed mathematics and computing.
2. Construct and analyse finite automata, regular expressions, context-free grammars and pushdown automata, and place languages in the Chomsky hierarchy.
3. Read and explain Turing's 1936 paper section by section, including computable numbers, description numbers, the universal machine and the diagonal argument.
4. Prove undecidability results by diagonalisation and by mapping reductions, and state and use Rice's theorem.
5. Relate Turing machines, the lambda calculus and recursive functions, and state the Church-Turing thesis precisely.
6. Define P, NP, NP-completeness, PSPACE and the hierarchy theorems, and carry out simple polynomial-time reductions.
7. Implement the central constructions of each topic as tested Common Lisp programs, version-controlled on GitHub.
8. Write a clear expository account of a primary source, citing it accurately.

## How Each Week Works

The learning experience is independent. Steps 1 to 6 are done by each learner on their own during the week; the Saturday meeting (next section) is where the group comes together.

1. **Read the primary source first** (a paper or section of a paper), slowly and with a pencil. Expect to reread.
2. **Read the textbook chapter** to see the modern formulation of the same ideas.
3. **Watch the lectures** for a second explanation.
4. **Do the Lisp practical in the terminal.** Keep one directory per week (`week-N/week-N.lisp`) with the code, a small test suite written with a macro you build in Week 1, and short answers to the reflection questions in comments. Run it with `clisp -q week-N.lisp`.
5. **Commit and push to GitHub** at the end of every work session, with a meaningful commit message, and tag the finished week (`week-N`). The commit history is part of your record of learning.
6. **Reflect** in a process journal: what did the original paper do differently from the textbook, and what did the code teach you that the proof did not?

## Weekly Meeting and Week Leads

Each week has one **week lead**. Leads are participants for Weeks 1 to 8 in order. The whole group meets every **Saturday, 4:00 to 5:00 pm** to go through that week's material. The meeting does not replace the independent reading, lectures or practical.

| Part | Time (suggested) | What happens |
|---|---|---|
| 1. Practical walkthrough | 4:00 to 4:30 pm | The lead walks the group through their own implementation of the week's Lisp practical and moderates the discussion. |
| 2. Content discussion | 4:30 to 5:00 pm | Open discussion of the content studied during the week: the primary source, the textbook chapter, the lectures and the focus questions. |

### The lead's role

- Present their implementation of the week's practical and moderate the discussion in Part 1.
- Review the other learners' submissions for the week (the `week-N` directory in their repositories). Whether to use AI to help with this review is the lead's choice.

### Everyone else

- Complete the week's reading and practical independently, and push the work to GitHub so the lead has submissions to review.
- Join both parts, and bring questions and observations from the week's reading to Part 2.

## Weekly Plan at a Glance

| Week | Week Lead | Theme | Primary Source | Lisp Practical |
|---|---|---|---|---|
| 1 | Yacouba | Infinity, Diagonalisation and the Entscheidungsproblem | Cantor (1891); Turing 1936, introduction and §1 | Terminal workbench (CLISP, Git), string enumeration, executable diagonal argument |
| 2 | Mamadou K. | Finite Automata and Regular Languages | Rabin and Scott (1959) | DFA/NFA simulators, subset construction, minimisation |
| 3 | Panga | Context-Free Languages and Pushdown Automata | Chomsky (1956) | Grammar engine, CNF conversion, CYK parser, PDA simulator |
| 4 | Sudoping | Turing Machines and Computable Numbers | Turing 1936, §§1-5 | Turing machine simulator, description numbers |
| 5 | Seb | The Universal Machine, the Halting Problem and the Entscheidungs problem | Turing 1936, §§6-8, 11; Church (1936) | Universal machine, diagonal construction, reductions |
| 6 | Yacouba | Lambda Calculus, Recursive Functions and Lisp | Church (1936); Turing's Appendix; McCarthy (1960) | Lambda reducer, mu-recursion, original Lisp eval |
| 7 | MK & Panga | Time Complexity, P and NP | Hartmanis and Stearns (1965); Cook (1971); Karp (1972) | SAT solver, verifiers, executable reductions |
| 8 | Diallo & Seb | Space, Hierarchies, Oracles and Capstone | Savitch (1970); Baker, Gill and Solovay (1975) | QBF, Savitch reachability, oracle machines, portfolio |

## Detailed Weekly Program

### Week 1: Infinity, Diagonalisation and the Entscheidungsproblem (*Foundations*)

**Week lead:** Yacouba · **Meeting:** Saturday, 4:00 to 5:00 pm

#### Primary reading

- Cantor (1891), *Über eine elementare Frage der Mannigfaltigkeitslehre*, the diagonal argument (any English translation or textbook presentation).
- Turing, *On Computable Numbers* (1936), introduction and §1, first pass only. Paper: [Proc. London Math. Soc., doi:10.1112/plms/s2-42.1.230](https://doi.org/10.1112/plms/s2-42.1.230); a free scan is at [cs.virginia.edu/~robins/Turing_Paper_1936.pdf](https://www.cs.virginia.edu/~robins/Turing_Paper_1936.pdf).
- Hilbert and Ackermann (1928), *Grundzüge der theoretischen Logik*, for the statement of the Entscheidungsproblem (summarised in the SEP entry below).

**Textbook:** Sipser, *Introduction to the Theory of Computation* (3rd ed.), Chapter 0 and the diagonalisation proof in §4.2.

**Lectures:** MIT OCW 18.404J *Theory of Computation* (Michael Sipser), opening lectures: [ocw.mit.edu/courses/18-404j-theory-of-computation-fall-2020](https://ocw.mit.edu/courses/18-404j-theory-of-computation-fall-2020/).

#### Focus

- Countable and uncountable sets; why there are more languages than programs.
- Alphabets, strings, languages and decision problems as membership questions.
- Hilbert's programme and what a decision procedure was meant to be.

#### Practical: the Lisp workbench and an executable diagonal argument

- Install GNU CLISP (for example `sudo apt install clisp`, `brew install clisp`, or the packages linked below) and start the REPL with `clisp`. Learn the terminal loop: `(load "week-1.lisp")` inside the REPL, `clisp -q week-1.lisp` for a script, and `clisp -q -x '(+ 1 2)'` for one-liners. Work through Graham chapters 2-6 and PAIP chapters 1-3 alongside.
- Set up Git and your GitHub repository (name to be decided): create a `week-1/` directory and a README, make a first commit, and push.
- Write a tiny test macro `check` (use `defmacro`) that reports pass or fail with the failing form. You will reuse it all program.
- Implement `nth-string` and its inverse `string-index`, a bijection between the natural numbers and all strings over an alphabet in shortlex order.
- Represent an infinite binary sequence as a function from naturals to 0 or 1. Given a function `enum` that returns the i-th sequence, build `diagonal` and test that it differs from each of the first 1000 sequences.
- Repeat for languages represented as predicates on strings: construct a language that is on no given list.

**Reflection:** Why does the diagonal argument fail for the rationals? Which exact step will Turing reuse in §8?

**Deliverable:** `week-1/week-1.lisp` with passing tests and written answers, pushed to your GitHub repository.

#### Resources

- [SEP: Computability and Complexity](https://plato.stanford.edu/entries/computability/)
- [Common Lisp HyperSpec](https://www.lispworks.com/documentation/HyperSpec/Front/)
- [GNU CLISP](https://clisp.sourceforge.io/)
- [Pro Git (free book)](https://git-scm.com/book) and [GitHub Docs](https://docs.github.com/)
- [Common Lisp Cookbook](https://lispcookbook.github.io/cl-cookbook/)

### Week 2: Finite Automata and Regular Languages (*Languages*)

**Week lead:** Mamadou K. · **Meeting:** Saturday, 4:00 to 5:00 pm

#### Primary reading

- Rabin and Scott (1959), *Finite Automata and Their Decision Problems*, IBM Journal of Research and Development 3(2), 114-125.
- Kleene (1956), *Representation of Events in Nerve Nets and Finite Automata*, for the origin of regular expressions (skim).

**Textbook:** Sipser Chapter 1 (DFAs, NFAs, regular expressions, pumping lemma). Optional: Kozen, *Automata and Computability*, lectures on Myhill-Nerode.

**Lectures:** the corresponding MIT 18.404J lectures on finite automata and regular expressions.

#### Focus

- Determinism versus nondeterminism and the subset construction.
- Closure properties and the equivalence of automata and regular expressions.
- The pumping lemma and Myhill-Nerode as tools for showing a language is not regular.

#### Practical: automata toolkit

- Define a DFA with `defstruct`; write `dfa-accepts-p`. Build DFAs for binary numbers divisible by 3 and for strings containing 0101.
- Write an NFA simulator with epsilon transitions by tracking sets of states.
- Implement `nfa->dfa` (subset construction) and test that both machines accept the same strings up to length 10.
- Implement the product construction for union and intersection, and complement. Decide language equivalence by testing emptiness of the symmetric difference.
- Implement DFA minimisation (table-filling or Moore's algorithm).
- Extension: parse a small regular-expression syntax and build an NFA (Thompson's construction).

**Reflection:** Which direction of Kleene's theorem did your code implement, and where could the number of states blow up?

**Deliverable:** `week-2/week-2.lisp` with tests, pushed to GitHub.

#### Resources

- Hopcroft, Motwani and Ullman, *Introduction to Automata Theory, Languages, and Computation*, Chapters 2-4.
- Graham chapter 4 (structures and hash tables) and PAIP chapter 6 (pattern matching and search tools).

### Week 3: Context-Free Languages and Pushdown Automata (*Grammars*)

**Week lead:** Panga · **Meeting:** Saturday, 4:00 to 5:00 pm

#### Primary reading

- Chomsky (1956), *Three Models for the Description of Language*, IRE Transactions on Information Theory 2(3), 113-124.

**Textbook:** Sipser Chapter 2 (context-free grammars, pushdown automata, pumping lemma for context-free languages, deterministic PDAs).

#### Focus

- Grammars as generators and as recognisers; ambiguity.
- Chomsky normal form and why it makes parsing tractable.
- The Chomsky hierarchy as the map for the rest of the program.

#### Practical: grammar engine and parsers

- Represent a grammar as a list of rules (see PAIP chapter 2 for the style). Write a random sentence generator with a depth bound, and an enumerator of all strings of length up to n.
- Convert a grammar to Chomsky normal form (remove epsilon rules, unit rules, long right-hand sides).
- Implement the CYK recognizer, first naively, then with memoisation (PAIP chapter 9).
- Write a nondeterministic PDA simulator that explores configurations breadth-first with a step bound. Test it on a^n b^n and even-length palindromes.
- Show on paper, then test empirically, why a^n b^n c^n resists your PDA.
- Extension: implement Earley parsing.

**Reflection:** What does the step bound in your PDA simulator hide, and how does that foreshadow undecidability?

**Deliverable:** `week-3/week-3.lisp` with tests, pushed to GitHub.

#### Resources

- PAIP chapters 2 and 9 (grammar and memoisation) and chapter 20 (unification grammars, optional).
- Hopcroft, Motwani and Ullman, Chapters 5-7.

### Week 4: Turing Machines and Computable Numbers (*Machines*)

**Week lead:** Sudoping · **Meeting:** Saturday, 4:00 to 5:00 pm

#### Primary reading

- Turing (1936), §§1-5: computing machines, definitions (circle-free machines, computable sequences and numbers), examples, abbreviated tables, enumeration of computable sequences. Read §9 for his argument that the definition captures effective calculation.
- Petzold, *The Annotated Turing* (Wiley, 2008), the chapters covering these sections, as a companion.

**Textbook:** Sipser Chapter 3 (Turing machines, variants, the definition of an algorithm). Optional: Soare, *Turing Computability*, introduction.

**Lectures:** MIT 18.404J lectures on Turing machines and the Church-Turing thesis.

#### Focus

- Turing's original model: m-configurations, scanned symbols, F-squares and E-squares.
- Why Turing defines numbers, not languages, and what circle-free means.
- Description numbers: a machine becomes an integer.
- The Church-Turing thesis as a thesis, not a theorem.

#### Practical: a Turing machine laboratory

- Implement a simulator with a sparse tape (hash table or two lists) and a transition table in Turing's quintuple style.
- Reproduce Turing's first example (prints 0 1 0 1 ... on alternate squares, the binary expansion of 1/3) and his second example (the sequence 001011011101111...). Read off the output from the F-squares after N steps.
- Write deciders in the modern style for 0^n 1^n and for palindromes.
- Implement `standard-description` and `description-number` using Turing's encoding (A for states, C for symbols, D as the marker, L, R, N and the semicolon, then the digits 1 to 7), and the inverse `machine-from-dn`. Test that every machine round-trips.
- Extension: simulate a two-tape machine on a one-tape machine and measure the slowdown.

**Reflection:** Turing's machines compute real numbers forever; Sipser's decide strings and halt. What is lost and gained in each view?

**Deliverable:** `week-4/week-4.lisp` with tests, pushed to GitHub and the printed first 50 digits of each example.

#### Resources

- [SEP: Turing Machines](https://plato.stanford.edu/entries/turing-machine/) and [SEP: The Church-Turing Thesis](https://plato.stanford.edu/entries/church-turing/)
- Davis (ed.), *The Undecidable* (Dover, 2004), which reprints Turing, Church, Gödel, Post and Kleene.

### Week 5: The Universal Machine, the Halting Problem and the Entscheidungsproblem (*Undecidability*)

**Week lead:** Seb · **Meeting:** Saturday, 4:00 to 5:00 pm

#### Primary reading

- Turing (1936), §§6-8 (the universal machine and the diagonal process) and §11 (the reduction of the Entscheidungsproblem).
- Church (1936), *A Note on the Entscheidungsproblem*, Journal of Symbolic Logic 1, 40-41. For the full argument, see *An Unsolvable Problem of Elementary Number Theory*, American Journal of Mathematics 58, 345-363.
- Skim Gödel (1931) via its summary in the SEP, to see how incompleteness and undecidability are related.

**Textbook:** Sipser Chapters 4 and 5 (decidability, the halting problem, mapping reductions, Rice's theorem, the Post correspondence problem).

#### Focus

- A single machine that simulates every machine.
- The diagonal argument turned on programs: no decider for halting exists.
- Mapping reductions as a way to transfer undecidability, and Rice's theorem as a general barrier.
- Turing's correction (1937) and why his proof concerns circle-free machines.

#### Practical: universality and undecidability

- Write `universal`, which takes a description number and an input and simulates the encoded machine for a given amount of fuel, reporting halted, accepted, or out of fuel.
- Make the diagonal argument concrete. Given any Lisp function claiming to decide halting, construct the program D that does the opposite on its own source, and run it against several plausible but wrong deciders. Show each one failing.
- Because Lisp code is data, write reductions as functions from program to program: A_TM to HALT_TM and A_TM to the emptiness problem.
- Write a bounded search for the Post correspondence problem, and note that it is only a semi-decision procedure.
- Extension: write a quine in Lisp and explain how it relates to Kleene's recursion theorem.

**Reflection:** Which assumption in your diagonal construction is the weakest in practice, and why does the proof still go through?

**Deliverable:** `week-5/week-5.lisp` with tests, pushed to GitHub and a half-page summary of how §11 reduces the Entscheidungsproblem to a question about machines.

#### Resources

- [SEP: Computability and Complexity](https://plato.stanford.edu/entries/computability/)
- Rice (1953), *Classes of Recursively Enumerable Sets and Their Decision Problems*, Transactions of the AMS 74.
- Post (1936), *Finite Combinatory Processes: Formulation 1*, Journal of Symbolic Logic 1.

### Week 6: Lambda Calculus, Recursive Functions and Lisp (*Models of Computation*)

**Week lead:** Yacouba · **Meeting:** Saturday, 4:00 to 5:00 pm

#### Primary reading

- Church (1936), *An Unsolvable Problem of Elementary Number Theory* (the sections defining lambda-definability).
- Turing (1936), Appendix: *Computability and Effective Calculability*, and Kleene (1936), *General Recursive Functions of Natural Numbers*, Mathematische Annalen 112.
- McCarthy (1960), *Recursive Functions of Symbolic Expressions and Their Computation by Machine, Part I*, Communications of the ACM 3(4), 184-195: [www-formal.stanford.edu/jmc/recursive.pdf](http://www-formal.stanford.edu/jmc/recursive.pdf).

**Textbook:** Sipser §3.3 on the Church-Turing thesis; Barendregt's *The Lambda Calculus* or Hindley and Seldin for reference. [SEP: The Lambda Calculus](https://plato.stanford.edu/entries/lambda-calculus/).

#### Focus

- Three independent definitions of computable (Turing machines, lambda-definable functions, general recursive functions) that coincide.
- Primitive recursion, minimisation (the mu operator), and why Ackermann's function is total but not primitive recursive.
- Where Lisp comes from: McCarthy's small set of primitives and its universal function.

#### Practical: three models and the original Lisp

- Lambda calculus: represent terms as s-expressions, implement capture-avoiding substitution and normal-order beta reduction with a step limit.
- Encode Church booleans, pairs, numerals, addition, multiplication and predecessor. Use the Z combinator (the strict-evaluation variant of Y) to define factorial.
- Write higher-order functions `primitive-recursion` and `mu` and use them to define addition, multiplication and a bounded search. Implement Ackermann and observe its growth.
- Write McCarthy's `eval` from the paper in Common Lisp using only `quote`, `atom`, `eq`, `car`, `cdr`, `cons`, `cond`, lambda and label. Then run your `eval` on a program that defines `eval`. Compare with PAIP chapter 22 (a Scheme interpreter).
- Extension: PAIP chapter 23 (a Lisp compiler) as a study of what interpreters hide.

**Reflection:** Which of the three models felt most natural to implement, and what does that suggest about why the Church-Turing thesis is believed?

**Deliverable:** `week-6/week-6.lisp` with tests, pushed to GitHub and a one-page note stating the Church-Turing thesis carefully.

#### Resources

- Abelson and Sussman, *Structure and Interpretation of Computer Programs*, Chapter 4 ([MIT Press, open access](https://mitpress.mit.edu/sites/default/files/sicp/index.html)).
- Graham chapters 6 and 10 (functions and macros).

### Week 7: Time Complexity, P and NP (*Complexity*)

**Week lead:** MK & Panga · **Meeting:** Saturday, 4:00 to 5:00 pm

#### Primary reading

- Hartmanis and Stearns (1965), *On the Computational Complexity of Algorithms*, Transactions of the AMS 117, 285-306.
- Cobham (1965) and Edmonds (1965, *Paths, Trees, and Flowers*) for polynomial time as the notion of tractability.
- Cook (1971), *The Complexity of Theorem-Proving Procedures*, STOC.
- Karp (1972), *Reducibility Among Combinatorial Problems*.

**Textbook:** Sipser Chapter 7 (time complexity, P, NP, NP-completeness, the Cook-Levin theorem) and §9.1 on hierarchy theorems. Optional: Arora and Barak, *Computational Complexity: A Modern Approach*, Chapter 2 (draft online at [theory.cs.princeton.edu/complexity](https://theory.cs.princeton.edu/complexity/)).

#### Focus

- Measuring resources and the robustness of P under reasonable model changes.
- NP as efficient verification; certificates.
- Polynomial-time reductions, NP-completeness, and the shape of the Cook-Levin proof.

#### Practical: SAT and executable reductions

- Represent a CNF formula as a list of clauses of signed integers. Write a verifier `sat-verify` that checks a certificate in polynomial time.
- Implement a brute-force SAT solver and then a DPLL solver with unit propagation and pure-literal elimination.
- Implement the reduction 3-SAT to INDEPENDENT-SET (or CLIQUE) as a function from formula to graph, and a function that maps a solution back to a satisfying assignment. Test round-trips.
- Time brute force versus DPLL on random instances of growing size using `get-internal-real-time` (or CLISP's `time` macro), and describe the growth you see.
- Extension: build the Cook-Levin tableau formula for a tiny Turing machine from Week 4.

**Reflection:** What does your timing experiment prove, and what can it never prove?

**Deliverable:** `week-7/week-7.lisp` with tests, pushed to GitHub, timing table and a short note on the experiment.

#### Resources

- [The Complexity Zoo](https://complexityzoo.net/)
- Papadimitriou, *Computational Complexity* (Addison-Wesley, 1994), Chapters 7-9.
- [SEP: Computational Complexity Theory](https://plato.stanford.edu/entries/computational-complexity/)
- Aaronson, [Why Philosophers Should Care About Computational Complexity](https://www.scottaaronson.com/papers/philos.pdf)

### Week 8: Space, Hierarchies, Oracles and Capstone (*Capstone*)

**Week lead:** Diallo & Seb · **Meeting:** Saturday, 4:00 to 5:00 pm

#### Primary reading

- Savitch (1970), *Relationships Between Nondeterministic and Deterministic Tape Complexities*, Journal of Computer and System Sciences 4.
- Stockmeyer and Meyer (1973), *Word Problems Requiring Exponential Time* (QBF and PSPACE-completeness).
- Baker, Gill and Solovay (1975), *Relativizations of the P=?NP Question*, SIAM Journal on Computing 4.
- Turing (1939), *Systems of Logic Based on Ordinals*, §4, where oracle machines first appear.

**Textbook:** Sipser Chapter 8 (space complexity, PSPACE, Savitch's theorem) and §9.2. Optional: Arora and Barak, Chapters 3-4 (diagonalisation, oracles, space complexity).

#### Focus

- Space versus time, and why nondeterminism costs only a square in space.
- The hierarchy theorems as diagonalisation with a clock.
- Oracles as a lens on proof techniques, and why diagonalisation alone cannot settle P versus NP.

#### Practical: space, oracles and portfolio

- Write a quantified Boolean formula evaluator by direct recursion over the quantifiers; note that it runs in polynomial space and exponential time.
- Implement Savitch-style reachability: decide whether t is reachable from s within k steps by trying every midpoint, and record the maximum recursion depth. Compare with breadth-first search in time and in depth.
- Add an oracle argument to your Week 5 simulator, so a machine can query membership in a set A. Build a relativised diagonal argument showing that the halting problem relative to A is not decidable relative to A.
- **Capstone:** assemble all weeks into one package (`defpackage :toc`) with a single test runner (a `Makefile` or shell script that calls `clisp`) and a README, all in your GitHub repository. Then either (a) write a 1,500-word essay, *Reading Turing 1936 ninety years on*, citing the paper section by section and your code, or (b) prepare a 15-minute talk that walks through one section of the paper with a live demo.

**Reflection:** Which theorem in the program surprised you most, and which of your programs best explains why it is true?

**Deliverable:** the `toc` package, `week-8/week-8.lisp`, and the capstone essay or talk outline.

#### Resources

- [The Complexity Zoo](https://complexityzoo.net/)
- Moore and Mertens, *The Nature of Computation* (Oxford University Press, 2011).
- Aaronson, *Quantum Computing since Democritus* (Cambridge University Press, 2013), early chapters.

## Additional Resources

### Core textbooks

- Sipser, *Introduction to the Theory of Computation* (Cengage).
- Hopcroft, Motwani and Ullman, *Introduction to Automata Theory, Languages, and Computation* (Pearson).
- Arora and Barak, *Computational Complexity: A Modern Approach* (Cambridge University Press).
- Kozen, *Automata and Computability* (Springer, 1997).

### Primary-source anthologies and companions

- Davis (ed.), *The Undecidable* (Dover, 2004).
- Petzold, *The Annotated Turing* (Wiley, 2008).
- Turing, *On Computable Numbers* (1936): [doi:10.1112/plms/s2-42.1.230](https://doi.org/10.1112/plms/s2-42.1.230); correction, Proc. London Math. Soc. 43 (1937), 544-546.
- Turing (1950), *Computing Machinery and Intelligence*, Mind 59 (optional enrichment).

### Common Lisp

- Graham, *ANSI Common Lisp* (Prentice Hall, 1996).
- Norvig, *Paradigms of Artificial Intelligence Programming*: [norvig.com/paip.html](https://norvig.com/paip.html) and [github.com/norvig/paip-lisp](https://github.com/norvig/paip-lisp).
- Seibel, *Practical Common Lisp*: [gigamonkeys.com/book](https://gigamonkeys.com/book/).
- [Common Lisp HyperSpec](https://www.lispworks.com/documentation/HyperSpec/Front/), [Common Lisp Cookbook](https://lispcookbook.github.io/cl-cookbook/), [GNU CLISP](https://clisp.sourceforge.io/).

### Terminal workflow and version control

- Run a file: `clisp -q file.lisp`; run and stay in the REPL: `clisp -q -i file.lisp`; evaluate an expression: `clisp -q -x '(expr)'`; compile: `clisp -c file.lisp`. CLISP is a bytecode implementation, so deep recursion and large searches in Weeks 6-8 may need `clisp -m 500MB` for more memory and careful, mostly iterative code.
- [Pro Git](https://git-scm.com/book) and [GitHub Docs](https://docs.github.com/).

### Online lectures and encyclopedia entries

- [MIT OCW 18.404J Theory of Computation](https://ocw.mit.edu/courses/18-404j-theory-of-computation-fall-2020/)
- [Stanford Encyclopedia of Philosophy](https://plato.stanford.edu/): entries on Turing machines, the Church-Turing thesis, the lambda calculus, computability and complexity.

## Habits to Maintain Throughout the Program

1. Read every primary source with a pencil, and write one sentence per section saying what it claims and what it assumes.
2. Write tests before the code. Your `check` macro from Week 1 should grow with you, and every push to GitHub should leave the tests passing.
3. Keep programs as data wherever you can: encodings, interpreters and reductions are all easier when Lisp code is just a list.
4. Keep a process journal: what the paper proved, what your code showed, and what is still unclear.
5. Commit small and often; write commit messages that say what you learned or fixed.
6. Explain one theorem aloud each week, to a study partner or to a rubber duck, without notes.

---

*Theory of Computation and the Foundations of Computing · 8-Week Program*

