Space information is represented by a single dimension `Coord`, whose elements are coordinates, i.e. 2-element `SVector(longitude, latitude)`. Each coordinate represents the center of an arbitrary polygon in space. The actual limits of each polygon are not included in the dimension for performance reasons.

In statistical functions such as [`spaceagg`](@ref), it is assumed that entry of the coordinates covers **an equal amount of area**. If this is not the case, you can simply provide an additional weights vector which would correspond to the area covered.

This dimension also allows indexing by latitude ranges, e.g. you can do

```julia
A # some `ClimArray` with a `Coord` dimension
A[Coord(Lat(-30..30)))]
```

Most functions of ClimateBase.jl implicitly assume that the coordinates are sorted by latidude. You can achieve this with the following code:

```julia
A # some `ClimArray` with a `Coord` dimension
coords = gnv(dims(A, Coord))
si = sortperm(coords; by = reverse)
A = A[Coord(si)]
```

**This is done automatically by [`ncread`](@ref).**
