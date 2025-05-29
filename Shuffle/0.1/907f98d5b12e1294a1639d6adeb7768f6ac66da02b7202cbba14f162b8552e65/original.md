```
nshuffle([rng=GLOBAL_RNG,], c, n::Integer, s::AbstractShuffle=RandomShuffle())
```

shuffle collection `c` `n` times using shuffling algorithm `s`. A random-number generator `rng` may be supplied for random shuffling algorithms. To shuffle `c` in-place see [`nshuffle!`](@ref)

# Examples

```jldoctest
julia> nshuffle(collect(1:8), 3, Faro{:in}())
8-element Array{Int64,1}:
 8
 7
 6
 5
 4
 3
 2
 1
```
