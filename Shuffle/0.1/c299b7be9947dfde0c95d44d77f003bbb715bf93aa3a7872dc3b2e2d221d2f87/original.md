```
nshuffle!([rng=GLOBAL_RNG,], c, n::Integer, s::AbstractShuffle=RandomShuffle())
```

shuffle collection `c` in-place `n` times using shuffling algorithm `s`. A random-number generator `rng` may be supplied for random shuffling algorithms.

# Examples

```jldoctest
julia> mt = MersenneTwister(1234);

julia> a = collect(1:7);

julia> nshuffle!(mt, a, 3, GilbertShannonReeds()); a
7-element Array{Int64,1}:
 5
 6
 1
 7
 2
 3
 4
```
