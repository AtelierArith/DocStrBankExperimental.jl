```
to_bcoords(pos, vel, o::Obstacle) -> ξ, sφ
```

Convert the real coordinates `pos, vel` to boundary coordinates (also known as Birkhoff coordinates) `ξ, sφ`, assuming that `pos` is on the obstacle.

`ξ` is the arc-coordinate, i.e. it parameterizes the arclength of the obstacle. `sφ` is the sine of the angle between the velocity vector and the vector normal to the obstacle.

The arc-coordinate `ξ` is measured as:

  * the distance from start point to end point in `Wall`s
  * the arc length measured counterclockwise from the open face in `Semicircle`s
  * the arc length measured counterclockwise from the rightmost point in `Circular`/`Ellipse`s

Notice that this function returns the *local* arclength. To get the global arclength parameterizing an entire billiard, simply do `ξ += arcintervals(bd)[i]` if the index of obstacle `o` is `i`.

See also [`from_bcoords`](@ref), which is the inverse function.
