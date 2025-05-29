```
I, E = quadde(f::Function, a::Real, b::Real, c::Real...;
              atol::Real=zero(Float64),
              rtol::Real=atol>0 ? zero(Float64) : sqrt(eps(Float64)))
```

Numerically integrate `f(x)` over an arbitrary interval [a, b] and return the integral value `I` and an estimated error `E`. The `E` is not exactly equal to the difference from the true value. However, one can expect that the integral value `I` is converged if `E <= max(atol, rtol*norm(I))` is true. Otherwise, the obtained `I` would be unreliable; the number of repetitions exceeds the `maxlevel` before converged. Optionally, one can divide the integral interval [a, b, c...], which returns `∫ f(x)dx in [a, b] + ∫f(x)dx in [b, c[1]] + ⋯`. It is worth noting that each endpoint allows discontinuity or singularity.

The integrand `f` can also return any value other than a scalar, as far as `+`, `-`, multiplication by real values, and `LinearAlgebra.norm`, are implemented. For example, `Vector` or `Array` of numbers are acceptable although, unfortunately, it may not be very performant.

# Examples

```jldoctest
julia> using DoubleExponentialFormulas

julia> using LinearAlgebra: norm

julia> f(x) = 2/(1 + x^2);

julia> I, E = quadde(f, -1, 1);

julia> I ≈ π
true

julia> E ≤ sqrt(eps(Float64))*norm(I)
true

julia> I, E = quadde(x -> [1/(1 + x^2), 2/(1 + x^2)], 0, Inf);

julia> I ≈ [π/2, π]
true

julia> E ≤ sqrt(eps(Float64))*norm(I)
true

julia> I, E = quadde(x -> 1/sqrt(abs(x)), -1, 0, 1);  # singular point at x = 0

julia> I ≈ 4
true

julia> E ≤ sqrt(eps(Float64))*norm(I)
true
```
