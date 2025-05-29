```
get_rydberg_params(h)
```

Returns a named tuple containing the fields `atoms`, `ϕ`, `Ω`, and `Δ` for the RydbergHamiltonian, `h`.

See also [`rydberg_h`](@ref)

# Example

`julia     (atoms,ϕ,Ω,Δ) = get_rydberg_params(h)``
