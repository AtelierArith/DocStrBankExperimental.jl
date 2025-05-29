```
spiral_energy(sys::System; k, axis)
```

Returns the energy of a generalized spiral phase associated with the propagation wavevector `k` (in reciprocal lattice units, RLU) and an `axis` vector that is normal to the polarization plane (in global Cartesian coordinates).

When $𝐤$ is incommensurate, this calculation can be viewed as creating an infinite number of periodic copies of `sys`. The spins on each periodic copy are rotated about the `axis` vector, with the angle $θ = 2π 𝐤⋅𝐫$, where `𝐫` denotes the displacement vector between periodic copies of `sys` in multiples of the lattice vectors of the chemical cell.

The return value is the energy associated with one periodic copy of `sys`. The special case $𝐤 = 0$ yields result is identical to [`energy`](@ref).

See also [`minimize_spiral_energy!`](@ref) and [`repeat_periodically_as_spiral`](@ref).
