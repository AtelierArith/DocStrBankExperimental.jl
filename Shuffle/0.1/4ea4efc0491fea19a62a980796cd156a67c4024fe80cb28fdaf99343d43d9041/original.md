```
shuffle([rng=GLOBAL_RNG,], c, s::AbstractShuffle=RandomShuffle())
```

shuffle collection `c` using shuffling algorithm `s`. To shuffle `c` in-place, see [`shuffle!`](@ref). A random-number generator `rng` may be supplied for random shuffling algorithms.

# Examples

```jldoctest
julia> mt = MersenneTwister(1234);

julia> shuffle(mt, [1, 2, 3, 4, 5, 6, 7, 8], GilbertShannonReeds())
8-element Array{Int64,1}:
 6
 7
 1
 2
 8
 3
 4
 5

julia> shuffle([6, 5, 4, 3, 2, 1], Faro{:in}())
6-element Array{Int64,1}:
 3
 6
 2
 5
 1
 4
```
