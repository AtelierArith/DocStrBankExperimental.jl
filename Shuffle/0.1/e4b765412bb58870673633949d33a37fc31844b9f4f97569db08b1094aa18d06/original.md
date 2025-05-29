```
AbstractShuffle
```

Supertype for [`AbstractDeterministicShuffle`](@ref) and [`AbstractRandomShuffle`](@ref).

# Implementation

New shuffling algorithm types should be sub types of either [`AbstractDeterministicShuffle`](@ref) or [`AbstractRandomShuffle`](@ref). If an algorithm can be defined in-place, only [`shuffle!`](@ref) needs to be extended. [`shuffle`](@ref), [`nshuffle`](@ref) and [`nshuffle!`](@ref) will make a copy / repeatedly call [`shuffle!`](@ref) as needed. If the algorithm can not be defined in-place, define [`shuffle`](@ref) and [`nshuffle!`](@ref). [`nshuffle`](@ref) will make a copy and call [`nshuffle!`](@ref).
