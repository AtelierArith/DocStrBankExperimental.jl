```
w(z::Real, spec::MSetting)
```

Weight function for M-estimation, where `spec` is a specification of which function to use. Computes ψ(z, spec)/z.

# Example

```julia
w(1.5, Huber(1.5, ϵ = 0.1))
w(1, Tukey(4.5, 6))
w(1.5, Andrew(4.5, 6))
w(1.5, Hampel([1, 3, 7])
```

See also [`ρ`](@ref ρ), [`ψ`](@ref ψ) and [`ψder`](@ref ψder).
