```
shuffle([rng=default_rng(),] v::AbstractArray)
```

Return a randomly permuted copy of `v`. The optional `rng` argument specifies a random number generator (see [Random Numbers](@ref)). To permute `v` in-place, see [`shuffle!`](@ref). To obtain randomly permuted indices, see [`randperm`](@ref).

# Examples

```jldoctest
julia> rng = MersenneTwister(1234);

julia> shuffle(rng, Vector(1:10))
10-element Vector{Int64}:
  6
  1
 10
  2
  3
  9
  5
  7
  4
  8
```
