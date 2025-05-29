Uses Chebyshev polynomials as basis functions to compute the weights in a hyperbolic cross polynomial approximation given the approximation sample, `y`, the `inverse interpolation matrix`. Returns a vector containing the weights in the hyperbolic cross polynomial.

# Signature

w = hyperbolic*cross*weights(y,inverse*interpolation*matrix)

# Example

```
julia> g,mi = hyperbolic_cross_grid(chebyshev_extrema,2,3,5,[1.0 1.0; 0.0 0.0])
julia> f(x) = sum(x.^2)
julia> y = [f(g[i,:]) for i in axes(g,1)]
julia> iim = hyperbolic_cross_inverse_interpolation_matrix(g,mi)
julia> w = hyperbolic_cross_weights(y,iim)
```
