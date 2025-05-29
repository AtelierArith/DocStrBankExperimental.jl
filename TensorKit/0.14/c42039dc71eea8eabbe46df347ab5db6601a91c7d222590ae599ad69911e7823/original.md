```
permute!(tdst::AbstractTensorMap, tsrc::AbstractTensorMap, (p₁, p₂)::Index2Tuple)
    -> tdst
```

Write into `tdst` the result of permuting the indices of `tsrc`. The codomain and domain of `tdst` correspond to the indices in `p₁` and `p₂` of `tsrc` respectively.

See [`permute`](@ref) for creating a new tensor and [`add_permute!`](@ref) for a more general version.
