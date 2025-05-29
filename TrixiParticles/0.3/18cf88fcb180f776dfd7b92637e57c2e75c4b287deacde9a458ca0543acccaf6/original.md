```
reset_wall!(rectangular_tank::RectangularTank, reset_faces, positions)
```

The selected walls of the tank will be placed at the new positions.

# Arguments

  * `reset_faces`: Boolean tuple of 4 (in 2D) or 6 (in 3D) dimensions, similar to `faces` in [`RectangularTank`](@ref).
  * `positions`: Tuple of new positions

!!! warning
    There are overlapping particles when adjacent walls are moved inwards simultaneously.

