```
Polynomial Tangent predictor
```

  * `n::Int64`: Order of the polynomial
  * `k::Int64`: Length of the last solutions vector used for the polynomial fit
  * `A::Matrix{T} where T<:Real`: Matrix for the interpolation
  * `tangent::BifurcationKit.AbstractTangentComputation`: Algo for tangent when polynomial predictor is not possible
  * `solutions::DataStructures.CircularBuffer`: Vector of solutions
  * `parameters::DataStructures.CircularBuffer{T} where T<:Real`: Vector of parameters
  * `arclengths::DataStructures.CircularBuffer{T} where T<:Real`: Vector of arclengths
  * `coeffsSol::Vector`: Coefficients for the polynomials for the solution
  * `coeffsPar::Vector{T} where T<:Real`: Coefficients for the polynomials for the parameter
  * `update::Bool`: Update the predictor by adding the last point (x, p)? This can be disabled in order to just use the polynomial prediction. It is useful when the predictor is called mutiple times during bifurcation detection using bisection.

# Constructor(s)

```
Polynomial(pred, n, k, v0)

Polynomial(n, k, v0)
```

  * `n` order of the polynomial
  * `k` length of the last solutions vector used for the polynomial fit
  * `v0` example of solution to be stored. It is only used to get the `eltype` of the tangent.

Can be used like

```
PALC(tangent = Polynomial(Bordered(), 2, 6, rand(1)))
```
