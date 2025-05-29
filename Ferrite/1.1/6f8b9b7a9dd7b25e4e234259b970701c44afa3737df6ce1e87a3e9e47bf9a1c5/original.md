```
PointLocation
```

Element of a [`PointIterator`](@ref), typically used to reinitialize [`PointValues`](@ref). Fields:

  * `cid::Int`: ID of the cell containing the point
  * `local_coord::Vec`: the local (reference) coordinate of the point
  * `coords::Vector{Vec}`: the coordinates of the cell
