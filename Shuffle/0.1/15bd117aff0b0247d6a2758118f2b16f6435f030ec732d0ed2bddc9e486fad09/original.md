```
RandomShuffle
```

type with no fields representing a completely random shuffle with singleton instance [`randshuffle`](@ref).

This algorithm is set as the default. See [`DEFAULTS`](@ref).

# Examples

```jldoctest
julia> mt = MersenneTwister(1234);

julia> shuffle(mt, 1:7, randshuffle)
7-element Array{Int64,1}:
 1
 2
 3
 7
 6
 4
 5

```
