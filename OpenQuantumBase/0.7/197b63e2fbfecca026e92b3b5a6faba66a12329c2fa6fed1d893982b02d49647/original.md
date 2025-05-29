```julia
check_density_matrix(ρ; atol, rtol)

```

Check whether matrix `ρ` is a valid density matrix. `atol` and `rtol` is the absolute and relative error tolerance to use when checking `ρ` ≈ 1.

# Examples

```julia-repl
julia> check_density_matrix(σx)
false
julia> check_density_matrix(σi/2)
true
```
