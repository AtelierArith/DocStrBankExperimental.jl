```
plot_planar_simplicial_morse(sc::LefschetzComplex,
                             coords::Vector{<:Vector{<:Real}},
                             fname::String,
                             morsesets::CellSubsets;
                             [hfac::Real=1.2,]
                             [vfac::Real=1.2,]
                             [sfac::Real=0,]
                             [pdim::Vector{Bool}=[false,true,true],]
                             [pv::Bool=false])
```

Create an image of a planar simplicial complex, together with Morse sets, or also selected multivectors.

The vector `coords` contains coordinates for every one of the vertices of the simplicial complex `sc`. The image will be saved in the file with name `fname`, and the ending determines the image type. Accepted are `.pdf`, `.svg`, `.png`, and `.eps`.

The vector `morsesets` contains a list of Morse sets, or more general, subsets of the simplicial complex. For every `k`, the set described by `morsesets[k]` will be shown in a distinct color.

The optional constants `hfac` and `vfac` contain the horizontal and vertical scale vectors for the margins, while `sfac` describes a uniform scale. If `sfac=0` the latter is automatically determined. The vector `pdim` specifies in which dimensions cells are drawn; the default only shows edges and triangles. Finally if one passes the argument `pv=true`, then in addition to saving the file a preview is displayed.
