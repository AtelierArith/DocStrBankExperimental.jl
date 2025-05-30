```
shuffle!([rng=default_rng(),] v::AbstractArray)
```

In-place version of [`shuffle`](@ref): randomly permute `v` in-place, optionally supplying the random-number generator `rng`.

# Examples

```jldoctest
julia> rng = MersenneTwister(1234);

julia> shuffle!(rng, Vector(1:16))
16-element Vector{Int64}:
  2
 15
  5
 14
  1
  9
 10
  6
 11
  3
 16
  7
  4
 12
  8
 13
```
