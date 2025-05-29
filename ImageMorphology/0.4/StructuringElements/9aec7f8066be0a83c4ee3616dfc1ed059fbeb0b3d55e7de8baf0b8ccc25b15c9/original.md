```
strel_box(A; r=1)
strel_box(size; r=size .÷ 2)
```

Construct the N-dimensional structuring element (SE) with all elements in the local window connected.

If image `A` is provided, then the SE size will be `(2r+1, 2r+1, ...)` with default half-size `r=1`. If `size` is provided, the default `r` will be `size .÷ 2`. The default `dims` will be all dimensions, that is, `(1, 2, ..., length(size))`.

```jldoctest; setup=:(using ImageMorphology; using ImageMorphology.StructuringElements)
julia> img = rand(64, 64);

julia> strel_box(img)
3×3 SEBoxArray{2, UnitRange{Int64}} with indices -1:1×-1:1:
 1  1  1
 1  1  1
 1  1  1

julia> strel_box(img; r=2)
5×5 SEBoxArray{2, UnitRange{Int64}} with indices -2:2×-2:2:
 1  1  1  1  1
 1  1  1  1  1
 1  1  1  1  1
 1  1  1  1  1
 1  1  1  1  1

julia> strel_box((5,5); r=(1,2))
5×5 SEBoxArray{2, UnitRange{Int64}} with indices -2:2×-2:2:
 0  0  0  0  0
 1  1  1  1  1
 1  1  1  1  1
 1  1  1  1  1
 0  0  0  0  0
```

!!! note "specialization and performance"
    The box shape `SEBox` is a special type for which many morphology algorithms may provide efficient implementations. For this reason, if one tries to collect an `SEBoxArray` into other array types (e.g. `Array{Bool}` via `collect`), then a significant performance drop is very likely to occur.


See also [`strel`](@ref) and [`strel_box`](@ref).
