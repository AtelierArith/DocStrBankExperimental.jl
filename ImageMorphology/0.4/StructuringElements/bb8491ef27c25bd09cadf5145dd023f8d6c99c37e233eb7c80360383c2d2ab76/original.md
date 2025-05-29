```
strel_diamond(A::AbstractArray, [dims]; r=1)
strel_diamond(size, [dims]; [r])
```

Construct the N-dimensional structuring element (SE) for a diamond shape.

If image `A` is provided, then the SE size will be `(2r+1, 2r+1, ...)` with default half-size `r=1`. If `size` is provided, the default `r` will be `maximum(size)÷2`. The default `dims` will be all dimensions, that is, `(1, 2, ..., length(size))`.

```jldoctest; setup=:(using ImageMorphology; using ImageMorphology.StructuringElements)
julia> img = rand(64, 64);

julia> strel_diamond(img) # default size for image input is (3, 3)
3×3 SEDiamondArray{2, 2, UnitRange{Int64}, 0} with indices -1:1×-1:1:
 0  1  0
 1  1  1
 0  1  0

julia> strel_diamond(img; r=2) # equivalent to `strel_diamond((5,5))`
5×5 SEDiamondArray{2, 2, UnitRange{Int64}, 0} with indices -2:2×-2:2:
 0  0  1  0  0
 0  1  1  1  0
 1  1  1  1  1
 0  1  1  1  0
 0  0  1  0  0

julia> strel_diamond(img, (1,)) # mask along dimension 1
3×1 SEDiamondArray{2, 1, UnitRange{Int64}, 1} with indices -1:1×0:0:
 1
 1
 1

julia> strel_diamond((3,3), (1,)) # 3×3 mask along dimension 1
3×3 SEDiamondArray{2, 1, UnitRange{Int64}, 1} with indices -1:1×-1:1:
 0  1  0
 0  1  0
 0  1  0
```

!!! note "specialization and performance"
    The diamond shape `SEDiamond` is a special type for which many morphology algorithms may provide much more efficient implementations. For this reason, if one tries to collect an `SEDiamondArray` into other array types (e.g. `Array{Bool}` via `collect`), then a significant performance drop is very likely to occur.


See also [`strel`](@ref) and [`strel_box`](@ref).
