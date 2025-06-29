```
IntegratedLimbDark(limbdark; N=21, basis=:legendre)
IntegratedLimbDark(u; kwargs...)
```

Computes the time-averaged flux in the middle of an exposure by wrapping a limb darkening law `limbdark` with a quadrature scheme. For each time step `t`, `N` extra points are *super-sampled* from `t-texp/2` to `t+texp/2`and the time-averaged flux is calculated via quadrature.

If a set of limb darkening coefficients, `u`, is provided, a [`PolynomialLimbDark`](@ref) law will be used by default.

# Mathematical form

$$
\bar{F}(t) = \frac{1}{\Delta t}\int_{t-\Delta t / 2}^{t+\Delta t / 2}{F(t')dt'}
$$

where $F$ is the wrapped limb darkening law and $\Delta t$ is the exposure time.

## Quadrature

The integration is approximated via [Guassian quadrature](https://en.wikipedia.org/wiki/Gaussian_quadrature)

$$
\frac{1}{\Delta t} \int{F(t')dt'} \approx \frac12\sum_i^N{w_i * F(\frac{\Delta t}{2}\xi_i + t)}
$$

where the weights `w_i` and nodes `ξ_i` are defined by the given quadrature rule. The nodes are defined by evaluating orthogonal polynomials `N` times between -1 and 1. Notice the change of interval required to go from the natural bounds of the orthogonal polynomial basis, `-1, 1`, to the range defined by the exposure time.

The following bases are available from [FastGaussQuadrature.jl](https://github.com/JuliaApproximation/FastGaussQuadrature.jl). In addition, a function can be passed which calculates `nodes, weights = f(N)`.

  * `:legendre` - Legendre polynomial base on the open `(-1, 1)`
  * `:radau` - Legendre polynomial base on the semi-open `[-1, 1)` interval
  * `:lobatto` - Legendre polynomial base on the closed `[-1, 1]` interval
