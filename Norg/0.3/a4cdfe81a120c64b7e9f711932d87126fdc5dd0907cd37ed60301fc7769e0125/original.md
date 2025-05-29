Easily parse Norg string to an AST. This can be used in *e.g.* Pluto notebooks, because `Base.show` has a method for "text/html" type mime for ASTs.

# Examples

```julia-repl
julia> norg"* Norg Header 1 Example"
NorgDocument
└─ (K"Heading1", 2, 11)
   └─ (K"ParagraphSegment", 4, 10)
      ├─ Norg
      ├─
      ├─ Header
      ├─
      ├─ 1
      ├─
      └─ Example
```
