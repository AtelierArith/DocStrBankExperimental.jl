```Julia
BilinearExponential(loc, scl, shp, skw)
BilinearExponential(p::AbstractVector)
struct BilinearExponential{T<:Real} <: ContinuousUnivariateDistribution
    A::T
    loc::T
    scl::T
    shp::T
    skw::T
end
```

A five-parameter pseudo-distribution which can be used to approximate various  asymmetric probability distributions found in geochronology (including as a result  of Bayesian eruption age estimation). 

This "bilinear exponential" distribution, as the name might suggest, is defined as an  exponential function with two log-linear segments, joined by an arctangent sigmoid:

$$
ℯ^{A} * ℯ^{v*xₛ*shp*skw - (1-v)*xₛ*shp/skw}
$$

where

$$
v = 1/2 - atan(xₛ)/π
$$

is a sigmoid, positive on the left-hand side, and

$$
xₛ = (x - loc)/scl
$$

is `x` scaled by the location parameter `loc` and scale parameter `scl`,  In addition to the scale parameter `scl`, the additional shape parameters `shp` and `skw`  (which control the sharpness and skew of the resulting distribution, respectively), are  all three required to be nonnegative.

If only four parameters `(loc, scl, shp, skw)` are specified, the normalization constant `A`  will be calculated such that the resulting distribution is normalized.
