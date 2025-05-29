```
MatchByBasinOverlap(threshold = Inf)
```

A matcher that matches IDs given full basins of attraction.

## Description

This matcher cannot be used in with the generic global continuation method of [`AttractorSeedContinueMatch`](@ref). This matcher matches IDs of attractors whose basins of attraction before and after `b₋, b₊` have the most overlap (in pixels). This overlap is normalized in 0-1 (with 1 meaning 100% of a basin in `b₋` is overlaping with some other basin in `b₊`). Therefore, the values this matcher compares are *full basins of attraction*, not attractors themselves (hence why it can't be given to [`AttractorSeedContinueMatch`](@ref)). Rather, you may use this matcher with [`matching_map`](@ref).

The `threshold` can dissallow matching between basins that do not have enough overlap. Basins whose overlap is less than `1/threshold` are guaranteed to get assined different IDs. For example: for `threshold = 2` basins that have ≤ 50% overlap get different IDs guaranteed. By default, there is no threshold.

The information of the basins of attraction is typically an `Array`, i.e., the direct output of [`basins_of_attraction`](@ref). For convenience, as well as backwards compatibility, when using [`matching_map`](@ref) with this mapper you may provide two `Array`s `b₊, b₋` representing basins of attraction after and before, and the conversion to dictionaries will happen internally as it is supposed to. To replace the `IDs` in `b₊` given the replacement map just call `replace!(b₊, rmap...)`, or use the in-place version [`matching_map!`](@ref) directly.

A lower-level input for this matcher in [`matching_map`](@ref) can be dictionaries mapping IDs to vectors of cartesian indices, where the indices mean which parts of the state space belong to which ID
