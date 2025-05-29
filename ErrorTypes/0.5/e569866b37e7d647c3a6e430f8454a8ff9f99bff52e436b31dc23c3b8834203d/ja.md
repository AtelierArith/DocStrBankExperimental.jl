```
flatten(x::Option{Option{T}})
```

`Option{Option{T}}`を`Option{T}`に変換します。

# 例

```jldoctest
julia> flatten(some(some("x")))
some("x")

julia> flatten(some(none(Float32)))
none(Float32)
```
