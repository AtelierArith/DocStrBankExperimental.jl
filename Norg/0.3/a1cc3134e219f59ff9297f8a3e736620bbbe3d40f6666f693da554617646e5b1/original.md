```
norg([codegentarget, ] s)
```

Parse the input `s` to an AST. If codegentarget is included, return the result of code generation for the given target.

# Examples

```julia-repl
julia> norg("* Hello world!")
NorgDocument
└─ (K"Heading1", 2, 8)
   └─ (K"ParagraphSegment", 4, 7)
      ├─ Hello
      ├─
      ├─ world
      └─ !
julia> norg(HTMLTarget(), "* Hello world!")
<div class="norg"><section id="section-h1-hello-world"><h1 id="h1-hello-world">Hello world&#33;</h1></section><section class="footnotes"><ol></ol></section></div>
```
