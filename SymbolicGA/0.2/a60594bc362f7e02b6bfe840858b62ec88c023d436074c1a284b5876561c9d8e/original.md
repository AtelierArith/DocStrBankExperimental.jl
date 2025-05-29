```
KVector{K,T,D,N}
```

Geometric `K`-vector with eltype `T` with `N` elements in a geometric algebra of dimension `D`.

The constructors `KVector{K,D}(elements...)` and `KVector{K,D}(elements::NTuple)` will automatically infer `T` from the arguments and `N` from `K` and `D`.

# Examples

```jldoctest
julia> KVector{1,3}(1.0, 2.0, 3.0)
KVector{1, Float64, 3, 3}(1.0, 2.0, 3.0)

julia> KVector{2,3}(1.0, 2.0, 3.0)
Bivector{Float64, 3, 3}(1.0, 2.0, 3.0)

julia> KVector{4,4}(1.0)
Quadvector{Float64, 4, 1}(1.0)
```
