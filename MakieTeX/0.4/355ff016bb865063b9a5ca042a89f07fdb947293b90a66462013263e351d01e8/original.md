```
TypstDocument(contents::AbstractString, add_defaults::Bool; preamble)
```

This constructor function creates a `struct` of type `TypstDocument`. All arguments are to be passed as strings.

If `add_defaults` is `false`, then we will *not* automatically add document structure. Note that in this case, keyword arguments will be disregarded and `contents` must be a complete Typst document.

Available keyword arguments are:

  * `preamble`: arbitrary code inserted prior to the `contents`.  Default: `""`.

See also [`CachedTypst`](@ref), [`compile_typst`](@ref), etc.
