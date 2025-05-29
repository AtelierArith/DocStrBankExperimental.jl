```
plot_planar_simplicial(sc::LefschetzComplex,
                       coords::Vector{<:Vector{<:Real}},
                       fname::String;
                       [mvf::CellSubsets=Vector{Vector{Int}}([]),]
                       [labeldir::Vector{<:Real}=Vector{Int}([]),]
                       [labeldis::Real=8,]
                       [hfac::Real=1.2,]
                       [vfac::Real=1.2,]
                       [sfac::Real=0,]
                       [pdim::Vector{Bool}=[true,true,true],]
                       [pv::Bool=false])
```

Create an image of a planar simplicial complex, and if specified, a Forman vector field on it.

The vector `coords` contains coordinates for every one of the vertices of the simplicial complex `sc`. The image will be saved in the file with name `fname`, and the ending determines the image type. Accepted are `.pdf`, `.svg`, `.png`, and `.eps`.

If the optional `mvf` is specified and is a Forman vector field, then this Forman vector field is drawn as well. The optional vector `labeldir` contains directions for the vertex labels, and `labeldis` the distance from the vertex. The directions have to be reals between 0 and 4, with 0,1,2,3 corresponding to E,N,W,S. The optional constants `hfac` and `vfac` contain the horizontal and vertical scale vectors, while `sfac` describes a uniform scale. If `sfac=0` the latter is automatically determined. The vector `pdim` specifies in which dimensions cells are drawn; the default shows vertices, edges, and triangles. Finally if one passes the argument `pv=true`, then in addition to saving the file a preview is displayed.

# Examples

Suppose we have created a simplicial complex using the commands

```julia
sc, coords = create_simplicial_delaunay(300, 300, 30, 20)
fname = "sc_plot_test.pdf"
```

Then the following code creates an image of the simplicial complex without labels, but with a preview:

```julia
plot_planar_simplicial(sc, coords, fname, pv=true)
```

If we want to see the labels, we can use

```julia
ldir = fill(0.5, sc.ncells);
plot_planar_simplicial(sc, coords, fname, labeldir=ldir, labeldis=10, pv=true)
```

This command puts all labels in the North-East direction at a distance of 10.
