```
LatticeWomble{T <: Number} <: Womble
```

A set of data (and co-ordinates) that are regularly arranged in space are of type `LatticeWomble` after having been passed through `wombling` - the fields in this type are

  * `m`, a *matrix* of rate of change at each (x,y) co-ordinate
  * `θ`, a *matrix* of direction of change at each (x,y) co-ordinate
  * `x` and `y`, the coordinates of the center of each cell

Note that the type of `x` and `y` should be the same as the element type of `m` and `θ`, because these values are all used when calculating the rate of change and that `x` and `y` correspond to latitude and longitude respectively.
