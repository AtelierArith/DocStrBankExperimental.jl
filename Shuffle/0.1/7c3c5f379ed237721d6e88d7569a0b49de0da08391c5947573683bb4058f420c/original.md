```
GilbertShannonReeds
```

type with no fields representing the [Gilbert-Shannon-Reeds](https://en.wikipedia.org/wiki/Gilbert–Shannon–Reeds_model) model of card shuffling. See singleton instance [`gsrshuffle`](@ref).

An in-place [`shuffle!`](@ref) is not implemented for this algorithm. However, an in-place [`nshuffle!`](@ref) is implemented.

# Examples

```jldoctest
julia> mt = MersenneTwister(1234);

julia> shuffle(mt, 1:7, gsrshuffle)
7-element Array{Int64,1}:
 5
 6
 1
 2
 7
 3
 4

```
