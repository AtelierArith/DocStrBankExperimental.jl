```
seg_img = fast_scanning(img, threshold, [diff_fn])
```

Segments the N-D image using a fast scanning algorithm and returns a [`SegmentedImage`](@ref) containing information about the segments.

# Arguments:

  * `img`         : N-D image to be segmented (arbitrary axes are allowed)
  * `threshold`   : Upper bound of the difference measure (δ) for considering                 pixel into same segment; an `AbstractArray` can be passed                 having same number of dimensions as that of `img` for adaptive                 thresholding
  * `diff_fn`     : (Optional) Function that returns a difference measure (δ)                 between the mean color of a region and color of a point

# Examples:

```jldoctest; setup = :(using ImageCore, ImageMorphology, ImageSegmentation)
julia> img = zeros(Float64, (3,3));

julia> img[2,:] .= 0.5;

julia> img[:,2] .= 0.6;

julia> seg = fast_scanning(img, 0.2);

julia> labels_map(seg)
3×3 Matrix{Int64}:
 1  4  5
 4  4  4
 3  4  6
```

# Citation:

Jian-Jiun Ding, Cheng-Jin Kuo, Wen-Chih Hong, "An efficient image segmentation technique by fast scanning and adaptive merging"
