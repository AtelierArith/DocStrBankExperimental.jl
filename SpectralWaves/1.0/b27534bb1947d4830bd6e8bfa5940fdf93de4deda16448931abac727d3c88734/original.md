```
fourier_transform(f::Vector{<:Number}, ω::Real, x::AbstractRange{<:Real})
```

Compute `f̂(ω)` using function values `f` at points `x`.

# Examples

```julia-repl
julia> f = [-1, 0, 1, 0, -1]; ω = 1; x = range(-π, π, length = 5);
julia> fourier_transform(f, ω, x)
0.5 + 0.0im
```
