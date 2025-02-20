<span lang="eo">

# Hari Potr kaj la Metodoj de Racionaleco

<!-- Por angligi, uzu tiun ĉi ŝablonon:
<details lang="en-GB">
<summary><i>Click to read this section in English</i></summary>
<blockquote>

[[ENGLISH TEXT HERE (yes the gaps are important!!!)]]

</blockquote>
</details>
-->

<details lang="en-GB">
<summary><i>Click to read this section in English</i></summary>
<blockquote>

***Harry Potter and the Methods Of Rationality***

Forked from
<https://github.com/rrthomas/hpmor>
Maintainer: Reuben Thomas <rrt@sc3d.org>

A LaTeX version of [the popular didactic fan-fiction](https://www.hpmor.com)
by Eliezer Yudkowsky, which can make e-books in PDF, ePub and Mobi formats,
and six PDF volumes that can be printed and bound. There are also dust
jackets for the printable volumes.

See [latest release](https://github.com/norwd/hpmor/releases/latest)
for PDF and e-book downloads.

TeXLive 2015 or later and git are required to build the book. (Note: the
book must be built from a git checkout.)

Note: the Omake Files chapters (11 and 64) have been moved to the end of the
single-file PDF. Those chapter numbers are omitted in the text, so chapter
10 is followed by chapter 12, for example. In the six-volume PDFs, all
chapters are renumbered to start from 1 at the start of a book, and there are
no appendices. Some epigraphs have been omitted but are in the source files
of the chapters.

</blockquote>
</details>

Prizorgita de Ruben Tomas, kaj tradukita de J. Mejer-Norŭud.

Ĉi tio estas [LaTeX]-a versio de [la populara didaktika fanfikcio][HPMOR] de Eliezer Judkaŭski,
kiu povas fariĝi bitlibrojn en multaj formatoj[^subtenataj-formatoj],
aŭ ses volumojn kiujn oni povas presi kaj bindi.
Ankaŭ estas polvkovriloj por la preseblaj volumoj.

[^subtenataj-formatoj]: Subtenataj formatoj estas PDF, ePub kaj Mobi.

Vidu [la lastan eldonon](https://github.com/norwd/hpmor/releases/latest) por elŝuti PDF-ojn kaj bitlibrojn.

Por kunmeti la libron, oni bezonas [TeXLive] (2015-a aŭ pli freŝa) kaj [git]. (Rimarku: la libro devas esti kunmetita de gitversikontrola elpreno)

Rimarku: en la originala libro estas bonusaĵoj (angle nomata "Omake Files"[^omake], t.e. ĉapitroj 11 kaj 64).
Tiuj ĉapitroj estas forigitaj ĉar ili estas nekanonaj (kaj ili ne estas parto de la rakonto).
Tial tiuj ĉapitraj numeroj estas ellasitaj en la teksto, do ekzemple ĉapitro 10 estas sekvata de ĉapitro 12.
En la ses-volumaj PDF-oj, ĉiuj ĉapitroj estas renumeritaj de 1 ĉe la komenco de la volumo, kaj ne estas apendicoj.
Kelkaj epigrafoj estas ellasitaj sed restas en la font-dosieroj de la ĉapitroj.

[^omake]: https://en.wikipedia.org/wiki/Omake

## Dosieroj

<details lang="en-GB">
<summary><i>Click to read this section in English</i></summary>
<blockquote>

***Files***

* `hpmor.tex` - the main file
* `layout/hp-format.tex` - mostly sets up memoir
* `layout/hp-markup.tex` - logical markup commands used in the text
* `chapters/` - one file per chapter, included from `hpmor.tex` and the
  individual volumes `hpmor-N.tex`.
* `spelling-list.txt` - a list of words used to spell-check the book.
* `fonts/` - various fonts used
* `latexmkrc` - configures latexmk to run LaTeX to build the PDFs.
* `GNUMakefile` - contains targets to make a Zip of the PDFs and release
  them to GitHub. (Mostly of interest to project maintainers.) `make all`
  does the same as `latexmk` (see below), which may be useful for editor
  integration (e.g. Emacs).
* `scripts/ebook/` - e-book generation scripts

</blockquote>
</details>

* `hpmor.tex` - la ĉefa dosiero.
* `layout/hp-format.tex` - plejparte agordas [memoir].
* `layout/hp-markup.tex` - logikaj markadaj komandoj uzataj en la teksto.
* `chapters/` - unu dosiero po ĉapitro, inkluzataj en `hpmor.tex` kaj la unuopaj volumoj `hpmor-N.tex`.
* `spelling-list.txt` - listo de vortoj uzataj por literumkorekti la libron.
* `fonts/` - diversaj tiparoj uzataj.
* `latexmkrc` - agordas [latexmk] por konstrui la PDF-ojn per [LaTeX].
* `GNUMakefile` - enhavas celojn por fari Zip-dosieron de la PDF-oj kaj eldoni ilin al GitHub. (Plejparte interesas projektajn prizorgantojn.) `make all` faras la samon kiel `latexmk` (vidu malsupre), kio povas esti utila por redaktila integriĝo (ekz. Emakso).
* `scripts/ebook/` - bitlibrgeneraciaj skriptoj.

## Kunmeti la libtro(j)

<details lang="en-GB">
<summary><i>Click to read this section in English</i></summary>
<blockquote>

***Building the book(s)***

If you do not want to install all requirements on your native system, you can run the build in a Docker container instead. See bottom of [Dockerfile](Dockerfile) for further info.

* `latexmk`: Build all PDFs. (If in doubt, just run this command and do
  something else for twenty minutes!)
* `make all`: Build a Zip of the PDFs.
* `latexmk hpmor`: Build the one-volume PDF `hpmor.pdf`
* `latexmk hpmor-N`: Build one of the six individual volumes
  `hpmor-1.pdf` to `hpmor-6.pdf`.
* `latexmk layout/hpmor-dust-jacket-N`: produce the dust jacket for Volume N,
  `hpmor-dust-jacket-N.pdf`. Note that this requires the corresponding
  volume, `hpmor-N.pdf`, to have been built first.
* `latexmk -c`: Remove files produced by building (except PDFs).
* `latexmk -C`: Remove files produced by building (including PDFs).

By default, the dust jackets assume 80gsm plain paper (this affects the
thickness of the book and hence the size of the dust jacket). This can be
configured in `layout/hp-paper-type.tex`; see `layout/papers.tex` for a
list of papers.

The exact sizes of dust jackets may vary; the current parameters were taken
from a commercial printer. They can be adjusted in `hp-dust-jacket.tex` as
desired.

Note that the back dust-flap is left for you to add your own text; edit
`layout/hp-dust-jacket.tex` and search for “PUT YOUR BACK DUST-FLAP TEXT HERE!”.
Make sure you remove the percent sign `%` at the start of the line, or your
text will not be printed. (This is a safety feature to make sure that if you
don’t change the text, the placeholder will not appear; instead, you’ll just
get a blank back flap.)

When producing a book with a dust jacket, you may well not want the front
cover as well. To suppress the front cover, use the following incantation:

`latexmk -norc -e '$options="nocover"' -r latexmkrc -g hpmor-1`

Of course, you can replace `hpmor-1` with any other volume, or leave it
out to generate all PDFs with no cover.

To build a single chapter, from the `chapters` directory use the command:

`latexmk -norc -e '$chapter="N"' -r ../latexmkrc -g hpmor-chapter-NNN`

Similarly, to build a single appendix or other non-chapter section, from the
top directory use the command:

`latexmk -norc -e '$chapterfile="FILENAME"' -r latexmkrc -g FILENAME`

</blockquote>
</details>

Se vi ne volas instali ĉiujn postulojn en via operaciumo, vi povas ruli la kunmetaĵon en Docker-ujo anstataŭe.
Vidu malsupron de [Dockerfile] por pliaj informoj.

* `latexmk`: Kunmetu ĉiujn PDF-ojn.
  (Se vi dubas, simple rulu ĉi tiu komando kaj faru ion alian dum dudek minutoj!)
* `make all`: Kunmetu Zip-dosieron de la PDF-oj.
* `latexmk hpmor`: Kunmetu la unu-voluman PDF-on `hpmor.pdf`
* `latexmk hpmor-N`: Kunmetu unu el la ses individuaj volumoj de `hpmor-1.pdf` ĝis `hpmor-6.pdf`.
* `latexmk layout/hpmor-dust-jacket-N`: Kunmetu la polvkovrilo por volumo N, `hpmor-dust-jacket-N.pdf`.
  Rimarku ke tiu komando bezonas la korespondantan volumon, `hpmor-N.pdf`.
* `latexmk -c`: Forigu dosierojn faritajn per kunmetado (krome PDF-ojn).
* `latexmk -C`: Forigu dosierojn faritajn per kunmetado (inkluzive krom).

Defaŭlte, la polvaj jakoj supozas 80-grama-po-kvadratmetran simplan paperon (ĉi tio influas la dikecon de la libro kaj do la grandecon de la polvkovrilo).
Ĉi tio povas esti agordita en `layout/hp-paper-type.tex`; vidu `layout/papers.tex` por listo de paperoj.

La precizaj grandecoj de polvkovriloj povas varii; la nunaj parametroj estis prenitaj de komerca presilo.
Ili povas esti alĝustigitaj en `hp-dust-jacket.tex` laŭdezire.

Kiam vi produktas libron kun polvkovrilo, vi eble ne volas ankaŭ la antaŭan kovrilon.
Por subpremi la antaŭan kovrilon, uzu la jenan komandon:

```
latexmk -norc -e '$options="nocover"' -r latexmkrc -g hpmor-1
```

Kompreneble, vi povas anstataŭigi `hpmor-1` per iu ajn alia volumo, aŭ forlasi ĝin por generi ĉiujn PDF-ojn sen kovrilo.

Por kunmeti ununuran ĉapitron, el la dosierujo `chapters/` rulu la komandon:

```
latexmk -norc -e '$chapter="N"' -r ../latexmkrc -g hpmor-chapter-NNN
```

Simile, por kunmeti ununuran apendicon aŭ alian ne-ĉapitran sekcion, el la supra dosierujo rulu la komandon:

```
latexmk -norc -e '$chapterfile="DOSIERNOMO"' -r latexmkrc -g DOSIERNOMO
```

## Kontribuado

<details lang="en-GB">
<summary><i>Click to read this section in English</i></summary>
<blockquote>

***Contributing***

Contributions are most welcome. These fall into the following categories:

1. Textual corrections (where the text differs from the online original
   unintentionally).
2. Textual improvements: fixing straight-up errors in the English (or
   deeper, the sense, story etc.), or “Britfixing”, i.e. replacing
   non-British usages.
3. Design and typography. Improvements to both the PDF and print versions of
   the books are encouraged. See the GitHub bug-tracker for known issues;
   also, search the sources for “FIXME”.
4. Translations. Translations are of course most welcome! A list of known
   translations and one or two hints are given below in the
   [next section](#translations).

For textual changes other than simple typo or language fixes, please
familiarise yourself with the style guide (below).

The preferred way to submit any improvement is as a GitHub pull request.
Textual corrections can also be submitted as issues in the issue tracker, or
by email to the maintainer.

For the GitHub URL, and email address of the maintainer, see above.

</blockquote>
</details>

Kontribuoj estas ja bonvenaj.
Ĉi tiuj kategoriiĝas jene:

1. Tekstaj koretoj.
   Kie la teksto malsamas de la reta originalo neintence.
1. Tekstaj plibonigoj.
   Riparado de rektajn erarojn en la angla (aŭ pli profunda, la senco, rakonto ktp.).
1. Dezajno kaj tipografio.
   Plibonigoj al kaj la PDF-aj kaj presitaj versioj de la libroj estas instigitaj.
   Vidu la cimspuradilon de GitHub por konataj problemoj; ankaŭ serĉu la fontojn por `FIXME` (t.e. "korektu min" en la angla).
1. Tradukoj.
   Tradukoj estas kompreneble plej bonvenaj! Listo de konataj tradukoj kaj iom da sugestoj estas donitaj en la [suba sekcio](#tradukoj).

Por tekstoj ŝanĝoj krom simplaj tajperaroj aŭ lingvaj korektoj, bonvolu konatiĝi kun je la [stilgvidilo](#stilgvidilo).

La preferata maniero sendi ajnan plibonigon estas tira peto ĉe GitHub.
Tekstaj korektoj ankaŭ povas esti proponataj kiel cimraportoj en la cimspuradilo, aŭ retpoŝte al la prizorganto.

## Stilgvidilo

<details lang="en-GB">
<summary><i>Click to read this section in English</i></summary>
<blockquote>

***Style guide***

### Spelling

When spell-checking, use `spelling-list.txt` instead of your personal
dictionary, so the results are less dependent on your setup. (The system
dictionary can still of course vary from one setup to another.)

Words that are standard English or part of the Harry Potter universe, or are
otherwise of “global” relevance should be added to `spelling-list.txt`.
Exclamations (“Eeeehhhh”) and other one-offs should be added to the per-file
word lists. (There’s obviously something of a grey area in the middle, e.g.
one-off references to various real and fictional people.)

Emacs users benefit from a `.dir-locals.el` that automatically sets up
`spelling-list.txt` as the personal dictionary for all HPMOR files.

### Chapter headings

Chapters that aren’t part of a continuing series look like this:

`\chapter{The Fundamental Attribution Error}`

Chapters that are part of a continuing series look like one of these:

`\partchapter{Working in Groups}{I}`

`\namedpartchapter{Self-Actualization}{SA}{VIII}{The Sacred and the Mundane}`

The first is pretty simple; it’s just the title of the chapter followed by
which part it is.

The second looks like the title of the chapter, then the abbreviation for
the title of the chapter, then the part, then the title of the part.

### First sentences

Normally, a chapter starts like this:

`\lettrine{P}{adma} Patil had finished`

That creates the large initial letter.

If the first paragraph of the chapter is all italics, though, it looks like
this:

    \begin{em}\lettrine{T}{he} red jet of fire took Hannah full in the
    [...]
    blazing green spirals brought down their foe’s Shield Charm.\par\end{em}

### Sections

`\section{Final Aftermath:}`

### Miscellaneous

There are some other things relating to newspaper headlines and such; check
the chapters they appear in for the appropriate markup.

### Markup

These are macros defined in `layout/hp-markup.tex`. You should glance
through that file to see what commands are available, and use them instead
of direct markup; for example `\shout` rather than `\textsc`.

</blockquote>
</details>

### Literumo

Por literumkontrolado, uzu `spelling-list.txt` anstataŭ via persona vortaro, do la rezultoj malpli dependas de via agordo.
(La sistemvortaro ankoraŭ povas kompreneble varii de unu aranĝo al alia.)

Vortoj kiuj estas parto de norma angla aŭ parto de la Harry Potter universo aŭ alie uzataj ĉie en la libro estu en la `spelling-list.txt`.
Ekkrioj (ekzemple "Eeeehhhh") kaj aliaj unufojoj estu en la po-dosiaj vortlistoj.
(Evidente estas io de griza areo en la mezo, ekz. unufojaj referencoj al diversaj realaj aŭ fikciaj homoj.)

Uzantoj de [Emakso] profitas de `.dir-locals.el` kiu aŭtomate ĝustigas `spelling-list.txt` kiel la persona vortaro por ĉiuj [HPMOR] dosieroj.

### Ĉapitrotitoloj

Ĉapitroj kiuj ne estas parto de daŭranta serio aspektas jene:

```
\chapter{La Fundamenta Atribuado Eraro}
```

Ĉapitroj kiuj estas parto de daŭranta serio aspektas jene:

```
\partchapter{Laborante en Grupoj}{I}
```

```
\namedpartchapter{Mem-Aktualigo}{MA}{VIII}{La Sankta kaj la Sekulara}
```

La unua estas sufiĉe simpla; ĝi estas nur la titolo de la ĉapitro sekvata de kiu parto ĝi estas.

La dua aspektas kiel la titolo de la ĉapitro, poste la mallongigo por la titolo de la ĉapitro, poste la parto, poste la titolo de la parto.

### Unuaj Frazoj

Normale, ĉapitro komenciĝas jene:

```
\lettrine{P}{adma} Patil finis sian vespermanĝon...
```

Tio kreas la grandan komencan literon.

Se la unua alineo de la ĉapitro estas kursiva, tiam ĝi aspektas jene:

```
\lettrine{L}{\emph{a}} \emph{ruĝa fajroĵeto trafis Hanna plene en la
[...]
ardantaj verdaj spiraloj faligis la Ŝilda Sorĉo de sian malamikon.}
```

### Sekcioj

```
\section{Fina Postsekvo:}
```

### Diversaĵoj

Estas kelkaj aliaj aferoj rilataj al la titoloj de gazetoj kaj tiaj; Rigardu la ĉapitrojn en kiuj tiuj titoloj estas por vidi kiel fari la markadon.

### Markado

Ĉi tiuj estas makrooj difinitaj en `layout/hp-markup.tex`.
Vi devus trarigardi tiun dosieron por vidi disponeblajn komandojn, kaj uzi ilin anstataŭ rekta markado; ekzemple `\shout` prefere ol `\textsc`.

## Tradukoj

<details lang="en-GB">
<summary><i>Click to read this section in English</i></summary>
<blockquote>

***Translations***

To translate the book, it is recommended to fork this repository, and check
back from time to time for updates. Also, do open an issue or PR against
this file to add the translation!

It is recommended to use `polyglossia` (not `babel`).

### Known translations

Note: there are other translations of HPMOR; here are listed only
translations of this edition.

* [English](https://github.com/rrthomas/hpmor) (original)
* [French](https://github.com/yeKcim/hpmor) (complete)
* [German](https://github.com/entorb/hpmor-de) (complete)
* [Esperanto](https://github.com/norwd/hpmor) (in progress)
  [![milestone details](https://img.shields.io/github/milestones/progress/norwd/hpmor/1?label=Chapters%20Completed)](https://github.com/norwd/hpmor/releases/tag/LaboroEnProgreso)

</blockquote>
</details>

Por traduki la libron, oni rekomendas projektforki ĉi tiun deponejon, kaj rerigardi de tempo al tempo por ĝisdatigoj.
Ankaŭ, bonvolu sugesti ŝanĝojn kontraŭ ĉi tiu dosiero por aldoni pliajn tradukojn!

Oni rekomendas uzi [polyglossia] (anstataŭ [babel]), sed [babel] funkcias pli bone por Esperantigado.

### Konataj tradukoj

Rimarku: ekzistas aliaj tradukoj de [HPMOR], jen estas listigataj nur tradukoj de tiu ĉi eldono.

* [Angla](https://github.com/rrthomas/hpmor) (originala)
* [Franca](https://github.com/yeKcim/hpmor) (kompleta)
* [Germana](https://github.com/entorb/hpmor-de) (kompleta)
* [Esperanta](https://github.com/norwd/hpmor) (ĉi tiu, en progreso)
  [![milestone details](https://img.shields.io/github/milestones/progress/norwd/hpmor/1?label=Ĉapitroj%20Kompletigitaj)](https://github.com/norwd/hpmor/releases/tag/LaboroEnProgreso)

<!-- Ligilaro / Links -->
[Dockerfile]: Dockerfile
[HPMOR]: http://www.hpmor.com
[LaTeX]: https://www.latex-project.org
[TeXLive]: https://www.tug.org/texlive
[git]: https://git-scm.com
[Emakso]: https://www.gnu.org/software/emacs
[memoir]: https://ctan.org/pkg/memoir
[latexmk]: https://ctan.org/pkg/latexmk
[polyglossia]: https://ctan.org/pkg/polyglossia
[babel]: https://ctan.org/pkg/babel
[babel-esperanto]: https://ctan.org/pkg/babel-esperanto

<!--  LocalWords:  hpmor tex hp txt latexmkrc latexmk GNUMakefile 80gsm '
 -->
<!--  LocalWords:  norc nocover N' NNN chapterfile FILENAME' Britfixing dir
 -->
<!--  LocalWords:  Eeeehhhh el partchapter namedpartchapter lettrine adma
 -->
<!--  LocalWords:  textsc
 -->

 </span>
