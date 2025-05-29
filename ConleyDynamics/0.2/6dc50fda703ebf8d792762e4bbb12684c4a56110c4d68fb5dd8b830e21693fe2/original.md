```
plot_planar_cubical(cc::LefschetzComplex,
                    coords::Vector{<:Vector{<:Real}},
                    fname::String;
                    [hfac::Real=1.2,]
                    [vfac::Real=1.2,]
                    [cubefac::Real=0,]
                    [pdim::Vector{Bool}=[true,true,true],]
                    [pv::Bool=false])
```

Create an image of a planar cubical complex.

The vector `coords` contains coordinates for every one of the vertices of the cubical complex `cc`. The image will be saved in the file with name `fname`, and the ending determines the image type. Accepted are `.pdf`, `.svg`, `.png`, and `.eps`. The optional constants `hfac` and `vfac` contain the horizontal and vertical scale vectors. The optional argument `cubefac` specifies the side length of an elementary cube for plotting, and it will be automatically determined otherwise. The vector `pdim` specifies which cell dimensions should be plotted, with `pdim[k]` representing dimension `k-1`. Finally if one passes the argument `pv=true`, then in addition to saving the file a preview is displayed.

# Examples

Suppose we have created a cubical complex using the commands

```julia
cubes = ["00.11", "01.01", "02.10", "11.10", "11.01", "22.00"]
coords = [[0,0],[0,1],[0,2],[1,0],[1,1],[1,2],[2,1],[2,2]]
cc = create_cubical_complex(cubes)
fname = "cc_plot_test.pdf"
```

Then the following code creates an image of the simplicial complex without labels, but with a preview:

```julia
plot_planar_cubical(cc, coords, fname, pv=true)
```

If one only wants to plot the edges in the complex, but not the vertices or rectangles, then one can use:

```julia
plot_planar_cubical(cc, coords, fname, pv=true, pdim=[false,true,false])
```
