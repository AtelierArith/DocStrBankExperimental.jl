```
function simplexgrid(coord::Array{Tc,2},
                     cellnodes::Array{Ti,2},
                     cellregions,
                     bfacenodes,
                     bfaceregions
                     ) where {Tc,Ti}
```

Create  d-dimensional simplex grid from five arrays.

  * coord: d $\times$ n_points matrix of coordinates
  * cellnodes: d+1 $\times$ n_tri matrix of triangle - point incidence
  * cellregions: n_tri vector of cell region markers
  * bfacenodes: d $\times$ n_bf matrix of boundary facet - point incidences
  * bfaceregions: n_bf vector of boundary facet  region markers

Coordinate type `Tc` index type `Ti` are detected from the first two parameters. `cellregions`, `bfaceregions`, `bfacenodes` are converted to have the same element type as `cellnodes`.
