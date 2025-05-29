```
flatten(x::Option{Option{T}})
```

Convert an `Option{Option{T}}` to an `Option{T}`.

# Examples

```jldoctest
julia> flatten(some(some("x")))
some("x")

julia> flatten(some(none(Float32)))
none(Float32)
```
