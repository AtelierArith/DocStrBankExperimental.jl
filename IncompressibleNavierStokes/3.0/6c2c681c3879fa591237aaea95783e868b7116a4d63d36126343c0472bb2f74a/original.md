Plot `state` field in pressure points. If `state` is `Observable`, then the plot is interactive.

Available fieldnames are:

  * `:velocity`,
  * `:vorticity`,
  * `:streamfunction`,
  * `:pressure`.

Available plot `type`s for 2D are:

  * `heatmap` (default),
  * `image`,
  * `contour`,
  * `contourf`.

Available plot `type`s for 3D are:

  * `contour` (default).

The `alpha` value gets passed to `contour` in 3D.
