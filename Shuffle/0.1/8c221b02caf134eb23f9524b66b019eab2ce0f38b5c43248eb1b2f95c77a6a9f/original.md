```
Cut(n::Integer)
```

represents a [cut](https://en.wikipedia.org/wiki/Cut_(cards)) at `n`, meaning elements up to and including `n` are moved to the bottom or end of a collection, while the rest shift up to the beginning.

No in-place [`shuffle!`](@ref) or [`nshuffle!`](@ref) exist for this shuffling type.

# Examples

```jldoctest
julia> shuffle([1, 2, 3, 4, 5, 6, 7], Cut(3))
7-element Array{Int64,1}:
 4
 5
 6
 7
 1
 2
 3
```
