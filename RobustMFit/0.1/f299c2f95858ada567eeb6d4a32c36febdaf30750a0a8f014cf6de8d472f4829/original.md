```
ρ(z::Real, spec::MSetting)
```

Loss function for M-estimation, where `spec` is a specification of which function to use.

# Example

```julia
ρ(1.5, Huber(1.5, ϵ = 0.1))
ρ(1, Tukey(4.5, 6))
ρ(1.5, Andrew(4.5, 6))
ρ(1.5, Hampel([1, 3, 7])
```

See also [`ψ`](@ref ψ), [`ψder`](@ref ψder) and [`w`](@ref w).
