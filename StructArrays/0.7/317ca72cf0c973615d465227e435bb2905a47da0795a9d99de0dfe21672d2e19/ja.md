```
LazyRows(s::StructArray)
```

`s`の[`LazyRow`](@ref)のイテレータ。

# 例

```julia-repl
julia> map(t -> t.b ^ t.a, LazyRows(t))
2-element Array{String,1}:
 "x"
 "yy"
```
