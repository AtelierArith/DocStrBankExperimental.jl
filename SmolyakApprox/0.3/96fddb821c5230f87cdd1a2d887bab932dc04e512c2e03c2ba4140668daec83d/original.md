Uses the `node_type` function to construct the `d`-dimensional full Smolyak grid with approximation layer `mu` and `domain`.  If `domain` is not provided, then the approximation domain defaults to [1.0,-1.0]^d. Returns the full Smolyak grid and the associated multi index.

# Signature

full*grid, mi = smolyak*grid*full(chebyshev*extrema,d,mu,domain)

# Examples

```
julia> full_grid, mi = smolyak_grid_full(chebyshev_extrema,2,2)
julia> full_grid, mi = smolyak_grid_full(chebyshev_extrema,2,[2,1])
julia> full_grid, mi = smolyak_grid_full(chebyshev_extrema,2,2,[3.0 1.5; 2.0 0.5])
julia> full_grid, mi = smolyak_grid_full(chebyshev_extrema,2,[2,2],[3.0 1.5; 2.0 0.5])
```
