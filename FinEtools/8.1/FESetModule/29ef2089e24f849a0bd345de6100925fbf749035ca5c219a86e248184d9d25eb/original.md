```
map2parametric(
    self::ET,
    x::Matrix{FT},
    pt::Vector{FT};
    tolerance = 0.001,
    maxiter = 5,
) where {ET<:AbstractFESet, FT}
```

Map a spatial location to parametric coordinates.

  * `x`=array of spatial coordinates of the nodes, size(x) = nbfuns x dim,
  * `c`= spatial location
  * `tolerance` = tolerance in parametric coordinates; default is 0.001.

# Return

  * `success` = Boolean flag, true if successful, false otherwise.
  * `pc` = Returns a row array of parametric coordinates if the solution was successful, otherwise NaN are returned.
