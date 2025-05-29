```julia
struct State{R<:Real}
```

Represents the current state of spatial configuration between two shapes (`A` and `B`) in 2-dimensional space. One of the shapes (`A`) is used as the frame of reference, thus residing at the origin with no rotation.

# Fields

  * `rel_pos::SVector{2,R}`: The position of `B` with respect to `A`.
  * `rel_rot::R`: The rotation of `B` with respect to `A`. Rotations are counter-clockwise measured from the positive x-axis, in radians.
