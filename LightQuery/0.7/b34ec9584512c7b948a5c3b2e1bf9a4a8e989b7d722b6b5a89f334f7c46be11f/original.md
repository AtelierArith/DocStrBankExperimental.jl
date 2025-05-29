```
By(sorted, key_function)
```

Mark that `sorted` has been pre-sorted by `key_function`. Use with [`Group`](@ref), and various joins.

```jldoctest
julia> using LightQuery


julia> using Test: @inferred


julia> @inferred By([1, -2], abs)
By{Array{Int64,1},typeof(abs)}([1, -2], abs)
```
