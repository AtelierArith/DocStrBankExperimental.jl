```
CachedTypst(doc::TypstDocument)
```

Compile a `TypstDocument`, compile it and return the cached Typst object.

A `CachedTypst` struct stores the document and its compiled form, as well as some pointers to in-program versions of it.  It also stores the page dimensions.

The constructor stores the following fields:

  * `doc`
  * `pdf`
  * `ptr`
  * `surf`
  * `dims`

!!! note
    This is a `mutable struct` because the pointer to the Poppler handle can change. TODO: make this an immutable struct with a Ref to the handle??  OR maybe even the surface itself...


!!! note
    It is also possible to manually construct a `CachedTypst` with `nothing` in the `doc` field,  if you just want to insert a pre-rendered PDF into your figure.

