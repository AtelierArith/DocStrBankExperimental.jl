```
add!(proj::L2Projector, set::AbstractVecOrSet{Int}, ip::Interpolation;
    qr_rhs, [qr_lhs])
```

Add an interpolation `ip` on the cells in `set` to the `L2Projector` `proj`.

  * `qr_rhs` sets the quadrature rule used to later integrate the right-hand-side of the projection equation, when calling [`project`](@ref). It should match the quadrature points used when creating the quadrature-point variables to project.
  * The *optional* `qr_lhs` sets the quadrature rule used to integrate the left-hand-side of the projection equation, and defaults to a quadrature rule that integrates the mass-matrix exactly for the given interpolation `ip`.
