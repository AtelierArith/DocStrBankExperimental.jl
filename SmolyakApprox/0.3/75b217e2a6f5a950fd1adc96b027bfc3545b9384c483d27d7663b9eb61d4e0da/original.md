Uses Chebyshev polynomials as basis functions to compute the weights in a Smolyak polynomial approximation given the approximation sample, `y`, the `inverse interpolation matrix`. Returns a vector containing the weights in the Smolyak polynomial.

# Signature

w = smolyak*weights(y,grid,inverse*interpolation_matrix)

# Example

```
julia> g,mi = smolyak_grid(chebyshev_extrema,2,2,[1.0 1.0; 0.0 0.0])
julia> f(x) = sum(x.^2)
julia> y = [f(g[i,:]) for i in axes(g,1)]
julia> iim = smolyak_inverse_interpolation_matrix(g,mi)
julia> w = smolyak_weights(y,iim)
```
