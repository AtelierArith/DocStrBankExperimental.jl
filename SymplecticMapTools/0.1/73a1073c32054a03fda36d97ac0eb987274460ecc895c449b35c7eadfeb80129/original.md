```
average_radius(z::FourierCircle)
```

Norm defined as the L2 norm of the radius, i.e. ‖z‖² = 1/2πp ∫ ||z(θ) - a₀||^2 dθ      = 1/2p ∑ₖ Tr(AₖᵀAₖ) If `i_circle = 0`, takes the norm over all circles. If `i_circle != 0`, finds the average radius of a single circle.
