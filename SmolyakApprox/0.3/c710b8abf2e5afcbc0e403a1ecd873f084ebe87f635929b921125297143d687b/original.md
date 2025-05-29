Uses Chebyshev polynomials as basis functions to compute the weights in a full Smolyak polynomial approximation given the approximation sample, `y`, the approximation `grid`, the `multi_index`, and the approximation  `domain` (defaults to [1.0,-1.0]^d).  Returns a vector of vectors containing the weights in the Smolyak polynomial.

# Signature

w = smolyak*weights*full(y,grid,multi_index,domain)

# Example

```
julia> g,mi = smolyak_grid_full(chebyshev_extrema,2,2,[1.0 1.0; 0.0 0.0])
julia> f(x) = sum(x.^2)
julia> y = [f(g[i,:]) for i in axes(g,1)]
julia> w = smolyak_weights_full(y,g,mi,[1.0 1.0; 0.0 0.0])
[[-0.625, -0.5, -0.125]
 [0.625, 0.49999999999999994, 0.12499999999999992, -1.6653345369377348e-16, 2.7755575615628914e-17]
 [-0.625, -0.5, -0.125]
 [0.75, 0.5, 0.125, 0.5, 0.0, 0.0, 0.125, 0.0, 0.0]
 [0.625, 0.49999999999999994, 0.12499999999999992, -1.6653345369377348e-16, 2.7755575615628914e-17]]
```
