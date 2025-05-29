```
QuadSS(T::Type{<:AbstractFloat}; maxlevel::Integer=10, h0::Real=one(T)/8)
```

A callable object to integrate a function over the range (-∞, ∞) using the *sinh-sinh quadrature*. It utilizes the change of variables to transform the integrand into a form well-suited to the trapezoidal rule.

`QuadSS` tries to calculate integral values `maxlevel` times at a maximum; the step size of a trapezoid is started from `h0` and is halved in each following repetition for finer accuracy. The repetition is terminated when the difference from the previous estimation gets smaller than a certain threshold. The threshold is determined by the runtime parameters, see below.

The type `T` represents the accuracy of interval. The integrand should accept values `x<:T` as its parameter.

---

```
I, E = (q::QuadSS)(f::Function;
                   atol::Real=zero(T),
                   rtol::Real=atol>0 ? zero(T) : sqrt(eps(T)))
                   where {T<:AbstractFloat}
```

Numerically integrate `f(x)` over the interval (-∞, ∞) and return the integral value `I` and an estimated error `E`. The `E` is not exactly equal to the difference from the true value. However, one can expect that the integral value `I` is converged if `E <= max(atol, rtol*norm(I))` is true. Otherwise, the obtained `I` would be unreliable; the number of repetitions exceeds the `maxlevel` before converged.

The integrand `f` can also return any value other than a scalar, as far as `+`, `-`, multiplication by real values, and `LinearAlgebra.norm`, are implemented. For example, `Vector` or `Array` of numbers are acceptable although, unfortunately, it may not be very performant.

# Examples

```jldoctest
julia> using DoubleExponentialFormulas

julia> using LinearAlgebra: norm

julia> qss = QuadSS(Float64);

julia> f(x) = 2/(1 + x^2);

julia> I, E = qss(f);

julia> I ≈ 2π
true

julia> E ≤ sqrt(eps(Float64))*norm(I)
true

julia> I, E = qss(x -> [1/(1 + x^2), 2/(1 + x^2)]);

julia> I ≈ [π, 2π]
true

julia> E ≤ sqrt(eps(Float64))*norm(I)
true
```
