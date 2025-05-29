```julia
struct CentroidDefuzzifier <: FuzzyLogic.AbstractDefuzzifier
```

Centroid defuzzifier. Given the aggregated output function $f$ and the output variable domain $[a, b]$ the defuzzified output is the centroid computed as

$$
\frac{∫_a^bxf(x)\textrm{d}x}{∫_a^bf(x)\textrm{d}x}.
$$

### Parameters

  * `N::Int64`: number of subintervals for integration, default 100.

## Algorithm

The integrals are computed numerically using the trapezoidal rule.
