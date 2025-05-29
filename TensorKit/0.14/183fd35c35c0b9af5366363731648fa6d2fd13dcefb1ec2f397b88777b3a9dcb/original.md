```
braid(tsrc::AbstractTensorMap, (p₁, p₂)::Index2Tuple, levels::IndexTuple;
      copy::Bool = false)
    -> tdst::TensorMap
```

Return tensor `tdst` obtained by braiding the indices of `tsrc`. The codomain and domain of `tdst` correspond to the indices in `p₁` and `p₂` of `tsrc` respectively. Here, `levels` is a tuple of length `numind(tsrc)` that assigns a level or height to the indices of `tsrc`, which determines whether they will braid over or under any other index with which they have to change places.

If `copy=false`, `tdst` might share data with `tsrc` whenever possible. Otherwise, a copy is always made.

To braid into an existing destination, see [braid!](@ref) and [`add_braid!`](@ref)
