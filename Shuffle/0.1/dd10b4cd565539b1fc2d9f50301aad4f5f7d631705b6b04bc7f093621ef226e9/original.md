```
Faro{S}
Weave{S}
```

Type with no fields representing the [Faro (weave)](https://en.wikipedia.org/wiki/Faro_shuffle) card shuffle where `S` can be `:in` for an in-shuffle or `:out` for an out-shuffle.

See singleton instances [`infaro`](@ref), [`outfaro`](@ref), [`inweave`](@ref), [`outweave`](@ref).

# Examples

```jldoctest
julia> shuffle([1, 2, 3, 4, 5, 6, 7, 8], Faro{:out}())
8-element Array{Int64,1}:
 1
 5
 2
 6
 3
 7
 4
 8

julia> nshuffle(collect(1:52), 26, inweave) == collect(52:-1:1)
true
```
