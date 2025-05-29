```
gamma(z)
```

Compute the gamma function for complex $z$, defined by

$$
\Gamma(z)
:=
\begin{cases}
    n!
    & \text{for} \quad z = n+1 \;, n = 0,1,2,\dots
    \\
    \int_0^\infty t^{z-1} e^{-t} \, \mathrm{d}t
    & \text{for} \quad \Re(z) > 0
\end{cases}
$$

and by analytic continuation in the whole complex plane.

# Examples

```jldoctest
julia> gamma(0)
Inf

julia> gamma(1)
1.0

julia> gamma(2)
1.0

julia> gamma(0.5)^2 ≈ π
true

julia> gamma(4 + 1) == prod(1:4) == factorial(4)
true
```

External links: [DLMF 5.2.1](https://dlmf.nist.gov/5.2.1), [Wikipedia](https://en.wikipedia.org/wiki/Gamma_function).

See also: [`loggamma(z)`](@ref SpecialFunctions.loggamma) for $\log \Gamma(z)$ and [`gamma(a,z)`](@ref SpecialFunctions.gamma(::Number,::Number)) for the upper incomplete gamma function $\Gamma(a,z)$.

# Implementation by

  * `Float`: C standard math library   [libm](https://en.wikipedia.org/wiki/C_mathematical_functions#libm).
  * `Complex`: by `exp(loggamma(z))`.
  * `BigFloat`: C library for multiple-precision floating-point [MPFR](https://www.mpfr.org/)
