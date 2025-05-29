```
transpose!(tdst::AbstractTensorMap, tsrc::AbstractTensorMap,
           (p₁, p₂)::Index2Tuple)
    -> tdst
```

Write into `tdst` the result of transposing the indices of `tsrc`. The codomain and domain of `tdst` correspond to the indices in `p₁` and `p₂` of `tsrc` respectively. The new index positions should be attainable without any indices crossing each other, i.e., the permutation `(p₁..., reverse(p₂)...)` should constitute a cyclic permutation of `(codomainind(tsrc)..., reverse(domainind(tsrc))...)`.

See [`transpose`](@ref) for creating a new tensor and [`add_transpose!`](@ref) for a more general version.
