```
Typst{T}
Typst(::T)
```

[`show(::IO, ::MIME"text/typst", ::Typst)`](@ref) に値を渡すために使用されるラッパーです。

# 例

```jldoctest
julia> Typst(1)
Typst{Int64}(1)

julia> Typst("a")
Typst{String}("a")
```
