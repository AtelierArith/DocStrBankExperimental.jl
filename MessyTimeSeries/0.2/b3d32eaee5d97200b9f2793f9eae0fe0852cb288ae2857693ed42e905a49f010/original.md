```
rand_without_replacement(rng::StableRNGs.LehmerRNG, nT::Int64, d::Int64)
```

Draw `length(P)-d` elements from the positional vector `P` without replacement.

`P` is permanently changed in the process.

# Examples

```jldoctest
julia> rand_without_replacement(StableRNG(1), 20, 5)
5-element Array{Int64,1}:
  1
  9
 14
 19
 20
```
