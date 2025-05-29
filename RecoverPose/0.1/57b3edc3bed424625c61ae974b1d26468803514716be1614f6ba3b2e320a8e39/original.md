```julia
triangulate(p1, p2, P1, P2)
```

Triangulate point given its two projection coordinates and projection matrices.

# Arguments:

  * `p1`: Pixel coordinates of a point in `(x, y)` format in the first view.
  * `p2`: Pixel coordinates of a point in `(x, y)` format in the second view.
  * `P1`: `3x4` or `4x4` projection matrix `K * P` for the first view.
  * `P2`: `3x4` or `4x4` projection matrix `K * P` for the second view.

# Returns:

Triangulated point in `(x, y, z, w)` format. To get actual coordinates, divide by `w`.
