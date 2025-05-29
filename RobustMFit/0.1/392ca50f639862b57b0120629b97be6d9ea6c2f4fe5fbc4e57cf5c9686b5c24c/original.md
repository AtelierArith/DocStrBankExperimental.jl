```
ψ(z::Real, spec::MSetting)
```

Derivative of loss function for M-estimation, where `spec` is a specification of which function to use.

# Example

```julia
ψ(1.5, Huber(1.5, ϵ = 0.1))
ψ(1, Tukey(4.5, 6))
ψ(1.5, Andrew(4.5, 6))
ψ(1.5, Hampel([1, 3, 7])
```

See also [`ρ`](@ref ρ), [`ψder`](@ref ψder) and [`w`](@ref w).
