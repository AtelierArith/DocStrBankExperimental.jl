Uses Chebyshev polynomials as basis functions to compute the weights in a hyperbolic cross polynomial approximation given the approximation sample, `y`, the approximation `grid`, the `multi_index`, and the approximation  `domain` (defaults to [-1.0,1.0]^d).  Returns a vector containing the weights in the hyperbolic cross polynomial.

# Signatures

w = hyperbolic*cross*weights(y,grid,multi*index) w = hyperbolic*cross*weights(y,grid,multi*index,domain)

# Example

```
julia> g,mi = hyperbolic_cross_grid(chebyshev_extrema,2,3,[7,5],[1.0 1.0; 0.0 0.0])
julia> f(x) = sum(x.^2)
julia> y = [f(g[i,:]) for i in axes(g,1)]
julia> w = hyperbolic_cross_weights(y,g,mi,[1.0 1.0; 0.0 0.0])
```
