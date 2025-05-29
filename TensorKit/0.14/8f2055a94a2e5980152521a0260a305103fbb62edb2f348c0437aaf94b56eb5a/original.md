```
permute(tsrc::AbstractTensorMap, (p₁, p₂)::Index2Tuple;
        copy::Bool=false)
    -> tdst::TensorMap
```

Return tensor `tdst` obtained by permuting the indices of `tsrc`. The codomain and domain of `tdst` correspond to the indices in `p₁` and `p₂` of `tsrc` respectively.

If `copy=false`, `tdst` might share data with `tsrc` whenever possible. Otherwise, a copy is always made.

To permute into an existing destination, see [permute!](@ref) and [`add_permute!`](@ref)
