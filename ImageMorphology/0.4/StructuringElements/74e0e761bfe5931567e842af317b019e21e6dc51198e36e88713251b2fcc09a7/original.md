```
strel_product(A, B, ...)
strel_product(se_list)
```

Cartesian product of multiple structuring elements; the output dimension `ndims(out) == sum(ndims, se_list)`.

See also [`strel_chain`](@ref) that chains SEs in the same dimension.

```jldoctest; setup=:(using ImageMorphology; using ImageMorphology.StructuringElements)
julia> strel_product(strel_diamond((5, 5)), centered(Bool[1, 1, 1]))
5×5×3 SEChainArray{3, OffsetArrays.OffsetArray{Bool, 3, BitArray{3}}} with indices -2:2×-2:2×-1:1:
[:, :, -1] =
 0  0  1  0  0
 0  1  1  1  0
 1  1  1  1  1
 0  1  1  1  0
 0  0  1  0  0

[:, :, 0] =
 0  0  1  0  0
 0  1  1  1  0
 1  1  1  1  1
 0  1  1  1  0
 0  0  1  0  0

[:, :, 1] =
 0  0  1  0  0
 0  1  1  1  0
 1  1  1  1  1
 0  1  1  1  0
 0  0  1  0  0
```
