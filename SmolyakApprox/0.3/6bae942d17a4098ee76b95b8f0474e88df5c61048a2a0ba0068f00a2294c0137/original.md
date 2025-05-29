Uses the `node_type` function to construt the `d`-dimensional Smolyak grid with approximation layer `mu` and `domain`.  If `mu` is an integer (vector of integers) the isotropic (ansiotropic) grid is constructed.  Returns the approximation grid and the associated multi-index.  If `domain` is not provided, then the approximation domain defaults to [1.0,-1.0]^d.

# Signatures

grid, multi*index = smolyak*grid(node*type,d,mu) grid, multi*index = smolyak*grid(chebyshev*extrema,d,mu,domain)

# Examples

```
julia> grid, m_index = smolyak_grid(chebyshev_extrema,2,2)
julia> grid, m_index = smolyak_grid(chebyshev_extrema,2,[2,1])
julia> grid, m_index = smolyak_grid(chebyshev_extrema,2,2,[3.0 1.5; 2.0 0.5])
julia> grid, m_index = smolyak_grid(chebyshev_extrema,2,[2,2],[3.0 1.5; 2.0 0.5])
```
