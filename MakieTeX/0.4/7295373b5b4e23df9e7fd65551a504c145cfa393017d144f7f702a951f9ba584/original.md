```
TEXDocument(contents::AbstractString, add_defaults::Bool; requires, preamble, class, classoptions)
```

This constructor function creates a `struct` of type `TEXDocument` which can be passed to `teximg`. All arguments are to be passed as strings.

If `add_defaults` is `false`, then we will *not* automatically add document structure. Note that in this case, keyword arguments will be disregarded and `contents` must be a complete LaTeX document.

Available keyword arguments are:

  * `requires`: code which comes before `documentclass` in the preamble.  Default: `raw"\RequirePackage{luatex85}"`.
  * `class`: the document class.  Default (and what you should use): `"standalone"`.
  * `classoptions`: the options you should pass to the class, i.e., `\documentclass[$classoptions]{$class}`.  Default: `"preview, tightpage, 12pt"`.
  * `preamble`: arbitrary code for the preamble (between `\documentclass` and `\begin{document}`).  Default: `raw"\usepackage{amsmath, xcolor} \pagestyle{empty}"`.

See also [`CachedTEX`](@ref), [`compile_latex`](@ref), etc.
