```
inverse_fourier_transform(f̂::Vector{<:Number}, ω::AbstractRange{<:Real}, x::Real)
```

Compute `f(x)` using expansion amplitudes `f̂` and eigenvalues `ω`.

# Examples

```julia-repl
julia> f̂ = [0.5, 0, 0.5]; ω = -1:1; x = π; inverse_fourier_transform(f̂, ω, x)
-1.0
```
