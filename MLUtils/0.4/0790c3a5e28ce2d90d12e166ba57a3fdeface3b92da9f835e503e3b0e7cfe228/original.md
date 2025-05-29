```
unstack(xs; dims)
```

Unroll the given `xs` into an array of arrays along the given dimension `dims`.

It is the inverse operation of [stack](https://docs.julialang.org/en/v1/base/arrays/#Base.stack).

See also [`unbatch`](@ref) and [`chunk`](@ref).

# Examples

```jldoctest
julia> unstack([1 3 5 7; 2 4 6 8], dims=2)
4-element Vector{Vector{Int64}}:
 [1, 2]
 [3, 4]
 [5, 6]
 [7, 8]
```
