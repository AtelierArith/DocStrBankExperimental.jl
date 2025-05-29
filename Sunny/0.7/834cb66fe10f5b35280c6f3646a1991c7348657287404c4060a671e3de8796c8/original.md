```
repeat_periodically_as_spiral(sys::System, counts::NTuple{3, Int}; k, axis)
```

Repeats the magnetic cell of [`System`](@ref) a number of times along each system axis according to the specified `counts`. Spins in each system image will be rotated according to the propagation wavevector `k` (in RLU) and the rotation `axis` (in global Cartesian coordinates). Coincides with [`repeat_periodically`](@ref) in the special case of `k = [0, 0, 0]`

See also [`minimize_spiral_energy!`](@ref) to find an energy-minimizing wavevector `k` and spin dipole configuration.

# Example

```julia
k = minimize_spiral_energy!(sys, axis; k_guess=randn(3))
repeat_periodically_as_spiral(sys, counts; k, axis)
```
