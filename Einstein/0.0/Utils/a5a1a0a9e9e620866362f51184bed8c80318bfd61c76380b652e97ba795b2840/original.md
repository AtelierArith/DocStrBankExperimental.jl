```
BarycentricInterpolation{TF<:AbstractFloat}(points::AbstractVector{TF}, weights::AbstractVector{TF})
```

A structure representing barycentric interpolation with precomputed weights.

# Fields

  * `points::AbstractVector{TF}`: Vector of interpolation points (typically Chebyshev points)
  * `weights::AbstractVector{TF}`: Vector of barycentric weights

# Methods

```
(itp::BarycentricInterpolation{TF})(values::AbstractVector{TFC}, x::TF) where {TF<:AbstractFloat,TFC<:Union{TF,Complex{TF}}}
```

Evaluate the interpolant at point `x` for function values.

# Reference

  * [chebfun/@chebtech2/bary.m at master · chebfun/chebfun](https://github.com/chebfun/chebfun/blob/master/%40chebtech2/bary.m)
  * [Berrut2004](@citet*)
