```
@typst_str("s")
typst"s"
```

Construct a [`TypstString`](@ref).

Control characters are escaped, except double quotation marks and backslashes in the same manner as `@raw_str`. Values may be interpolated by calling the `TypstString` constructor, except using a backslash instead of the type name. Interpolation syntax may be escaped in the same manner as quotation marks.

!!! tip
    Print directly to an `IO` using [`show(::IO, ::MIME"text/typst", ::Typst)`](@ref).

    See also the performance tip to [Avoid string interpolation for I/O](https://docs.julialang.org/en/v1/manual/performance-tips/#Avoid-string-interpolation-for-I/O).


# Examples

```jldoctest
julia> x = 1;

julia> typst"$ \(x; mode = math) / \(x + 1; mode = math) $"
typst"$ 1 / 2 $"

julia> typst"\(x//2)"
typst"$1 / 2$"

julia> typst"\(x // 2; mode = math)"
typst"(1 / 2)"

julia> typst"\\(x)"
typst"\\(x)"
```
