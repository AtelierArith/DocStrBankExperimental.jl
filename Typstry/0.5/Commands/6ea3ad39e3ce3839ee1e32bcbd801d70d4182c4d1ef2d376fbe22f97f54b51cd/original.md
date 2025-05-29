```
render(value;
    input = "input.typ",
    output = "output.pdf",
    open = true,
    ignorestatus = true,
    preamble = preamble,
context...)
```

Render to a document using [`show(::IO, ::MIME"text/typst", ::Typst)`](@ref).

This first generates the `input` file containing the [`preamble`](@ref) and formatted `value`. Then it is compiled to the `output` document, whose format is inferred by its file extension to be `pdf`, `png`, or `svg`. The document may be automatically `open`ed by the default viewer. The [`ignorestatus`](@ref) flag may be set. This supports using the [`julia_mono`](@ref) typeface.

# Examples

```jldoctest
julia> render(Any[true 1; 1.2 1 // 2]);
```
