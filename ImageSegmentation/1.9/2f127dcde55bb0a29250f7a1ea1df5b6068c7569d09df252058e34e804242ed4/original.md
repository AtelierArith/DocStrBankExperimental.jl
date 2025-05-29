```
seg_img = unseeded_region_growing(img, threshold, [kernel_dim], [diff_fn])
seg_img = unseeded_region_growing(img, threshold, [neighbourhood], [diff_fn])
```

Segments the N-D image using automatic (unseeded) region growing algorithm and returns a [`SegmentedImage`](@ref) containing information about the segments.

# Arguments:

  * `img`             :  N-D image to be segmented (arbitrary axes are allowed)
  * `threshold`       :  Upper bound of the difference measure (δ) for considering                      pixel as the same segment
  * `kernel_dim`      :  (Optional) `Vector{Int}` having length N or a `NTuple{N,Int}`                      whose ith element is an odd positive integer representing                      the length of the ith edge of the N-orthotopic neighbourhood
  * `neighbourhood`   :  (Optional) Function taking CartesianIndex{N} as input and                      returning the neighbourhood of that point.
  * `diff_fn`         :  (Optional) Function that returns a difference measure (δ)                      between the mean color of a region and color of a point

# Examples

```jldoctest; setup = :(using ImageCore, ImageMorphology, ImageSegmentation)
julia> img = zeros(Gray{N0f8},4,4);

julia> img[2:4,2:4] .= 1;

julia> seg = unseeded_region_growing(img, 0.2);

julia> labels_map(seg)
4×4 Matrix{Int64}:
 1  1  1  1
 1  2  2  2
 1  2  2  2
 1  2  2  2
```
