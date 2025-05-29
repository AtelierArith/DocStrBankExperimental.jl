```
function simplexgrid(coord::Array{Tc,2},
                     cellnodes::Array{Ti,2},
                     cellregions,
                     bfacenodes,
                     bfaceregions,
                     bedgenodes,
                     bedgeregions
                     ) where {Tc,Ti}
```

Create simplex grid from coordinates, cell-nodes-adjancency, cell-region-numbers, boundary-face-nodes adjacency, boundary-face-region-numbers, boundary-edge-nodes, and boundary-edge-region-numbers arrays.

The index type `Ti` is detected from `cellnodes`, all other arrays besides `coord` are converted to this index type.
