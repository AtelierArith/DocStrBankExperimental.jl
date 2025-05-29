```
EdgePoint{T<:Integer}
```

A point along the edge between two OSM nodes.

# Fields

  * `n1::T`: First node of edge.
  * `n2::T`: Second node of edge.
  * `pos::Float64`: Position from `n1` to `n2`, from 0 to 1.
