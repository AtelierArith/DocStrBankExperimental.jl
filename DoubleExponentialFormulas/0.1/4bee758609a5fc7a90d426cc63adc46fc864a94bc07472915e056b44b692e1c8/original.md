```
QuadDE(T::Type{<:AbstractFloat}; maxlevel::Integer=10, h0::Real=one(T)/8)
```

A callable object to integrate an function over an arbitrary interval, which uses the *double exponential formula*s also known as the *tanh-sinh quadrature* and its variants. It utilizes the change of variables to transform the integrand into a form well-suited to the trapezoidal rule.

`QuadDE` tries to calculate integral values `maxlevel` times at a maximum; the step size of a trapezoid is started from `h0` and is halved in each following repetition for finer accuracy. The repetition is terminated when the difference from the previous estimation gets smaller than a certain threshold. The threshold is determined by the runtime parameters, see below.

The type `T` represents the accuracy of interval. The integrand should accept values `x<:T` as its parameter.

---

```
I, E = (q::QuadDE{T})(f::Function, a::Real, b::Real, c::Real...;
                      atol::Real=zero(T),
                      rtol::Real=atol>0 ? zero(T) : sqrt(eps(T)))
                      where {T<:AbstractFloat}
```

Numerically integrate `f(x)` over an arbitrary interval [a, b] and return the integral value `I` and an estimated error `E`. The `E` is not exactly equal to the difference from the true value. However, one can expect that the integral value `I` is converged if `E <= max(atol, rtol*norm(I))` is true. Otherwise, the obtained `I` would be unreliable; the number of repetitions exceeds the `maxlevel` before converged. Optionally, one can divide the integral interval [a, b, c...], which returns `∫f(x)dx in [a, b] + ∫f(x)dx in [b, c[1]] + ⋯`. It is worth noting that each endpoint allows discontinuity or singularity.

The integrand `f` can also return any value other than a scalar, as far as `+`, `-`, multiplication by real values, and `LinearAlgebra.norm`, are implemented. For example, `Vector` or `Array` of numbers are acceptable although, unfortunately, it may not be very performant.

# Examples

```jldoctest
julia> using DoubleExponentialFormulas

julia> using LinearAlgebra: norm

julia> qde = QuadDE(Float64);

julia> f(x) = 2/(1 + x^2);

julia> I, E = qde(f, -1, 1);

julia> I ≈ π
true

julia> E ≤ sqrt(eps(Float64))*norm(I)
true

julia> g(x) = [1/(1 + x^2), 2/(1 + x^2)];

julia> I, E = qde(g, 0, Inf);

julia> I ≈ [π/2, π]
true

julia> E ≤ sqrt(eps(Float64))*norm(I)
true

julia> h(x) = 1/sqrt(abs(x));  # singular point at x = 0

julia> I, E = qde(h, -1, 0, 1);

julia> I ≈ 4
true

julia> E ≤ sqrt(eps(Float64))*norm(I)
true
```
