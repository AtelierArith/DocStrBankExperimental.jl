```
load_grid(images::Vector{<:SpmImage}, by::Function=im -> im.z
name::AbstractString="Z", unit::AbstractString="m";
only_overlap::Bool=false, header_only::Bool=false)::SpmGrid
```

Loads a grid from a stack of images. The sweep signal is specified with the `by` argument, as well as `name` and `unit`. The first image determines the pixel density, as well as the channels that will be available. Here, the backward channels will be associated with the backward scan direciton in the images. Ideally, all images should have the same pixel density and recorded channels. if `only_overlap` is true, then data is returned only for the pixels that are overlapping in all images. If `header_only` is `true`, then only the header is created.
