```
label_flatzones(img; [dims])
label_flatzones(img; se)
```

Find the flat zones in image 'img'. Flat zones are defined as connected (respect to se) voxels that have the same value.

The `dims` keyword is used to specify the dimension to process by constructing the box shape structuring element [`strel_box(img; dims)`](@ref strel_box). For generic structuring element, the half-size is expected to be either `0` or `1` along each dimension.

The output `labeled image` is an integer array.
