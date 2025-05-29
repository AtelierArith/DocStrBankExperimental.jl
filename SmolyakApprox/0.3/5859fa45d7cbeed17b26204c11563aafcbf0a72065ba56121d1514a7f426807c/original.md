Computes a Smolyak polynomial given the `node` in the approximation grid, the `multi-index`, and the approximation `domain` (defaults to [-1.0,1.0]^d). Returns a vector containing the basis functions in the polynomial evaluated at `node`.

# Signature

spoly = smolyak*polynomial(node,multi*index,domain)

# Example

```
julia> g,mi = smolyak_grid(chebyshev_extrema,2,2,[1.0 1.0; 0.0 0.0])
julia> node = g[5,:]
julia> sploy = smolyak_polynomial(node,mi,[1.0 1.0; 0.0 0.0])
```
