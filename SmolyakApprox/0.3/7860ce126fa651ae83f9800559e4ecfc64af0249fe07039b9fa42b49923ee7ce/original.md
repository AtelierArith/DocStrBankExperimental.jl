Uses Chebyshev polynomials as basis functions to compute using multi-threading the inverse interpolation matrix for a Smolyak polynomial approximation given the approximation grid, `grid`, the `multi_index`, and the  approximation `domain` (defaults to [1.0,-1.0]^d).  Returns a matrix containing the inverse interoplation matrix.

# Signature

iim = smolyak*inverse*interpolation*matrix*threaded(grid,multi_index,domain)

# Example

```
julia> g,mi = smolyak_grid(chebyshev_extrema,2,2,[1.0 1.0; 0.0 0.0])
julia> iim = smolyak_inverse_interpolation_matrix_threaded(g,mi)
```
