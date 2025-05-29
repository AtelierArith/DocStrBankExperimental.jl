```
shuffle!([rng=GLOBAL_RNG,], c, s::AbstractShuffle=RandomShuffle())
```

shuffle collection `c` in-place using shuffling algorithm `s`. A random-number generator `rng` may be supplied for random shuffling algorithms.

# Examples

```jldoctest
julia> mt = MersenneTwister(1234);

julia> a = collect(1:6);

julia> shuffle!(mt, a); a
6-element Array{Int64,1}:
 2
 1
 3
 6
 4
 5

julia> shuffle!(a, Faro{:out}()); a
6-element Array{Int64,1}:
 2
 6
 1
 4
 3
 5
```
