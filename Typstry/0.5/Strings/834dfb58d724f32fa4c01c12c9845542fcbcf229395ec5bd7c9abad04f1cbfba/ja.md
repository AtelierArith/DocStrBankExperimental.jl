```
TypstText{T}
TypstText(::Any)
```

`[`show_typst`](@ref)` メソッドが `print` を使用するラッパーです。

# 例

```jldoctest
julia> TypstText(1)
TypstText{Int64}(1)

julia> TypstText("a")
TypstText{String}("a")
```
