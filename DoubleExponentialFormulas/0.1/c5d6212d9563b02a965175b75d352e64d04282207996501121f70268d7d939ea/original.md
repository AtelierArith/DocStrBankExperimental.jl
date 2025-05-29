```
quaddeo(f::Function, ω::Real, θ::Real, a::Real, b::Real;
        h0::Real=one(ω)/5, maxlevel::Integer=12,
        atol::Real=zero(ω),
        rtol::Real=atol>0 ? zero(atol) : sqrt(eps(typeof(atol))))
```

Numerically integrate `f(x)` over an arbitrary interval [a, b] and return the integral value `I` and an estimated error `E`. The `quaddeo` function is specialized for the decaying oscillatory integrands,

```
f(x) = f₁(x)sin(ωx + θ),
```

where `f₁(x)` is a decaying algebraic function. `ω` and `θ` are the frequency and the phase of the oscillatory part of the integrand. If the oscillatory part is `sin(ωx)`, then `θ = 0.0`; if it is `cos(ωx)` instead, then `θ = π/(2ω)`. The `E` is not exactly equal to the difference from the true value. However, one can expect that the integral value `I` is converged if `E <= max(atol, rtol*norm(I))` is true. Otherwise, the obtained `I` would be unreliable; the number of repetitions exceeds the `maxlevel` before converged. Optionally, one can divide the integral interval [a, b, c...], which returns `∫ f(x)dx in [a, b] + ∫f(x)dx in [b, c[1]] + ⋯`.  It is worth noting that each endpoint allows discontinuity or singularity.

The integrand `f` can also return any value other than a scalar, as far as `+`, `-`, multiplication by real values, and `LinearAlgebra.norm`, are implemented. For example, `Vector` or `Array` of numbers are acceptable although, unfortunately, it may not be very performant.

# Examples

```jldoctest
julia> using DoubleExponentialFormulas

julia> using LinearAlgebra: norm

julia> f(x) = sin(x)/x;

julia> I, E = quaddeo(f, 1.0, 0.0, 0.0, Inf);

julia> I ≈ π/2
true

julia> E ≤ sqrt(eps(Float64))*norm(I)
true
```
