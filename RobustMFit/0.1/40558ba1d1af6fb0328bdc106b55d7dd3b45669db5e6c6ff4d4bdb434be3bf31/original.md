```
ψder(z::Real, spec::MSetting)
```

Second derivative of loss function for M-estimation, where `spec` is a specification of which function to use.

# Example

```julia
ψder(1.5, Huber(1.5, ϵ = 0.1))
ψder(1, Tukey(4.5, 6))
ψder(1.5, Andrew(4.5, 6))
ψder(1.5, Hampel([1, 3, 7])
```

See also [`ρ`](@ref ρ), [`ψ`](@ref ψ) and [`w`](@ref w).
