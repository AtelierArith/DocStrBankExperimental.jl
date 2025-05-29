```julia
SmolyakParameters(B)
SmolyakParameters(B, M)

```

Parameters for Smolyak grids that are *independent of the dimension of the domain*.

Polynomials are organized into blocks (of eg `1, 2, 2, 4, 8, 16, …`) polynomials (and corresponding gridpoints), indexed with a *block index* `b` that starts at `0`. `B ≥ ∑ bᵢ` and `0 ≤ bᵢ ≤ M` constrain the number of blocks along each dimension `i`.

`M > B` is not an error, but will be normalized to `M = B` with a warning.
