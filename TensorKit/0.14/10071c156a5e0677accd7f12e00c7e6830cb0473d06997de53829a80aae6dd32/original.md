```
braid!(tdst::AbstractTensorMap, tsrc::AbstractTensorMap,
       (p₁, p₂)::Index2Tuple, levels::Tuple)
    -> tdst
```

Write into `tdst` the result of braiding the indices of `tsrc`. The codomain and domain of `tdst` correspond to the indices in `p₁` and `p₂` of `tsrc` respectively. Here, `levels` is a tuple of length `numind(tsrc)` that assigns a level or height to the indices of `tsrc`, which determines whether they will braid over or under any other index with which they have to change places.

See [`braid`](@ref) for creating a new tensor and [`add_braid!`](@ref) for a more general version.
