```
filled_img = imfill(img::AbstractArray{Bool}, interval; dims=coords_spatial(img))
filled_img = imfill(img::AbstractArray{Bool}, interval, connectivity)
```

Connected components of an image is found using flood-fill algorithm and returns a copy of the original image after filling objects that falls in the range of interval. For filling objects, represent the holes (part to be filled) with `true` in your array.

Parameters:

  * img            = Input image (Boolean array type)
  * interval       = objects of size (# of voxels) in this range will be filled with `false`
  * connectivity   = a Boolean-valued connectivity pattern, see [`label_components`](@ref).

# Examples

```jldoctest; setup=:(using ImageMorphology)
julia> img = Bool[0 0 1 1 0 0;
                  0 1 0 1 1 0;
                  0 0 1 1 0 0]
3×6 Matrix{Bool}:
 0  0  1  1  0  0
 0  1  0  1  1  0
 0  0  1  1  0  0

julia> imfill(.!(img), 0:3)
3×6 BitMatrix:
 1  1  0  0  1  1
 1  0  0  0  0  1
 1  1  0  0  1  1

julia> .!(ans)
3×6 BitMatrix:
 0  0  1  1  0  0
 0  1  1  1  1  0
 0  0  1  1  0  0
```
