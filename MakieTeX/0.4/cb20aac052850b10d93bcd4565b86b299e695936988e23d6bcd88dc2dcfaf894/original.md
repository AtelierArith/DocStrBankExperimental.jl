```
CachedTEX(doc::TEXDocument; kwargs...)
```

Compile a `TEXDocument`, compile it and return the cached TeX object.

A `CachedTEX` struct stores the document and its compiled form, as well as some pointers to in-program versions of it.  It also stores the page dimensions.

In `kwargs`, one can pass anything which goes to the internal function `compile_latex`. These are primarily:

  * `engine =`lualatex`/`xelatex`/...`: the LaTeX engine to use when rendering
  * `options=`-file-line-error``: the options to pass to`latexmk`.

The constructor stores the following fields:

  * `doc`
  * `pdf`
  * `ptr`
  * `surf`
  * `dims`

!!! note
    This is a `mutable struct` because the pointer to the Poppler handle can change. TODO: make this an immutable struct with a Ref to the handle??  OR maybe even the surface itself...


!!! note
    It is also possible to manually construct a `CachedTEX` with `nothing` in the `doc` field,  if you just want to insert a pre-rendered PDF into your figure.

