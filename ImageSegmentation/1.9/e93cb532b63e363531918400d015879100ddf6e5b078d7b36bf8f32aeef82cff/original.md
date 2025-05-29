```
segments                = watershed(img, markers; compactness, mask)
```

Segments the image using watershed transform. Each basin formed by watershed transform corresponds to a segment. If you are using image local minimas as markers, consider using [`hmin_transform`](@ref) to avoid oversegmentation.

Parameters:

  * img            = input grayscale image
  * markers        = An array (same size as img) with each region's marker assigned a index starting from 1. Zero means not a marker.                     If two markers have the same index, their regions will be merged into a single region.                     If you have markers as a boolean array, use `label_components`.
  * compactness    = Use the compact watershed algorithm with the given compactness parameter. Larger values lead to more regularly                     shaped watershed basins.[^1]
  * mask           = Only segment pixels where the value of `mask` is true, used to restrict segmentation to only areas of interest

[^1]: https://www.tu-chemnitz.de/etit/proaut/publications/cws*pSLIC*ICPR.pdf

# Example

```jldoctest; setup = :(using ImageCore, ImageMorphology, ImageSegmentation)
julia> seeds = falses(100, 100); seeds[50, 25] = true; seeds[50, 75] = true;

julia> dists = distance_transform(feature_transform(seeds)); # calculate distances from seeds

julia> markers = label_components(seeds); # give each seed a unique integer id

julia> results = watershed(dists, markers);

julia> labels_map(results); # labels of segmented image
```
