```
seg_img = seeded_region_growing(img, seeds, [kernel_dim], [diff_fn])
seg_img = seeded_region_growing(img, seeds, [neighbourhood], [diff_fn])
```

Segments the N-D image `img` using the seeded region growing algorithm and returns a [`SegmentedImage`](@ref) containing information about the segments.

# Arguments:

  * `img`             :  N-D image to be segmented (arbitrary axes are allowed)
  * `seeds`           :  `Vector` containing seeds. Each seed is a Tuple of a                      CartesianIndex{N} and a label. See below note for more                      information on labels.
  * `kernel_dim`      :  (Optional) `Vector{Int}` having length N or a `NTuple{N,Int}`                      whose ith element is an odd positive integer representing                      the length of the ith edge of the N-orthotopic neighbourhood
  * `neighbourhood`   :  (Optional) Function taking CartesianIndex{N} as input and                      returning the neighbourhood of that point.
  * `diff_fn`         :  (Optional) Function that returns a difference measure(δ)                      between the mean color of a region and color of a point

!!! note
    The labels attached to points must be positive integers, although multiple points can be assigned the same label. The output includes a labelled array that has same indexing as that of input image. Every index is assigned to either one of labels or a special label '0' indicating that the algorithm was unable to assign that index to a unique label.


# Examples

```jldoctest; setup = :(using ImageCore, ImageMorphology,ImageSegmentation)
julia> img = zeros(Gray{N0f8},4,4);

julia> img[2:4,2:4] .= 1;

julia> seeds = [(CartesianIndex(3,1),1),(CartesianIndex(2,2),2)];

julia> seg = seeded_region_growing(img, seeds);

julia> labels_map(seg)
4×4 Matrix{Int64}:
 1  1  1  1
 1  2  2  2
 1  2  2  2
 1  2  2  2
```

# Citation:

Albert Mehnert, Paul Jackaway (1997), "An improved seeded region growing algorithm", Pattern Recognition Letters 18 (1997), 1065-1071
