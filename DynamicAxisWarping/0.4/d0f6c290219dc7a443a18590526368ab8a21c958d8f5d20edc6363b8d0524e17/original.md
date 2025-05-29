```
iterative_gdtw!(data; max_iters = data.max_iters, verbose = data.verbose) -> cost
```

Runs the GDTW algorithm with iterative refinement for `max_iters` iterations, returning the resulting cost. Uses the [`GDTWWorkspace`](@ref) in `data.cache` and updates the `data.warp` vector. Here, `data` is usually obtained by [`prepare_gdtw`](@ref).

This can be called multiple times on the same `data` with a higher value of `max_iters` to refine a calculation without starting over, which can be useful for checking convergence.

## Example

```julia
data = prepare_gdtw(x,y; max_iters = 3)
cost3 = iterative_gdtw!(data) # performs 3 iterations, returns the cost
cost10 = iterative_gdtw!(data; max_iters = 10) # performs 7 more iterations, returns the cost
ϕ, ψ = gdtw_warpings(data)

# Equivalently,
cost10, ϕ, ψ = gdtw(x,y; max_iters = 10)
```
