```
plot_planar_cubical_morse(cc::LefschetzComplex,
                          coords::Vector{<:Vector{<:Real}},
                          fname::String,
                          morsesets::CellSubsets;
                          [hfac::Real=1.2,]
                          [vfac::Real=1.2,]
                          [cubefac::Real=0,]
                          [pdim::Vector{Bool}=[false,true,true],]
                          [pv::Bool=false])
```

Create an image of a planar cubical complex, together with Morse sets, or also selected multivectors.

The vector `coords` contains coordinates for every one of the vertices of the cubical complex `cc`. The image will be saved in the file with name `fname`, and the ending determines the image type. Accepted are `.pdf`, `.svg`, `.png`, and `.eps`.

The vector `morsesets` contains a list of Morse sets, or more general, subsets of the cubical complex. For every `k`, the set described by `morsesets[k]` will be shown in a distinct color.

The optional constants `hfac` and `vfac` contain the horizontal and vertical scale vectors for the margins, while `cubefac` describes a uniform scale. If `cubefac=0` the latter is automatically determined. The vector `pdim` specifies in which dimensions cells are drawn; the default only shows edges and squares. Finally if one passes the argument `pv=true`, then in addition to saving the file a preview is displayed.
