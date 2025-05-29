```julia
Chebyshev(grid_kind, N)

```

`N` Chebyshev polynomials (of the first kind) on $[-1, 1]$, with the associated grid of `grid_kind`.

# Example

```julia
basis = Chebyshev(InteriorGrid(), 10)
```
