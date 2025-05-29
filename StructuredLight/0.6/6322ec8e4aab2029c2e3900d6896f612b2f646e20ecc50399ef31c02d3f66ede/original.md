```
free_propagation(ψ, x, y, z [, scaling]; k=1)
```

Propagate an inital profile `ψ`.

The propagation is the solution of `∇² ψ + 2ik ∂_z ψ = 0` at distance `z` under the initial condition `ψ`.

`x` and `y` are the grids over which `ψ` is calculated.

If `z` is an `AbstractArray`, the output is a 3D array representing the solution at every element of `z`.

The output at a distance `z[n]` is calculated on a scalled grid defined by `scaling[n] * x` and `scaling[n] * y`.

`k` is the wavenumber.

# Example

```jldoctest
x = LinRange(-10, 10, 256)
y = LinRange(-10, 10, 512)
z = LinRange(0.1, 1, 10)

ψ = hg(x, y; m=3, n=2)
ψ′ = hg(2x, 2y; m=3, n=2)

(
    free_propagation(ψ, x, y, z) ≈ stack(free_propagation(ψ, x, y, z) for z ∈ z)
    &&
    free_propagation(ψ, x, y, z, fill(2, length(z))) ≈ stack(free_propagation(ψ, x, y, z, 2) for z ∈ z)
    &&
    free_propagation(ψ, x, y, 0.5, 2) ≈ free_propagation(ψ′, 2x, 2y, 0.5)
)

# output
true
```
