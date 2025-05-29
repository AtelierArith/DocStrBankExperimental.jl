```
strel_product(A, B, ...)
strel_product(se_list)
```

複数の構造要素の直積; 出力次元 `ndims(out) == sum(ndims, se_list)`。

同じ次元でSEを連結する [`strel_chain`](@ref) も参照してください。

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
