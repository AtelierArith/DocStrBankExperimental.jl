```
solve!(cb, solver, b; kwargs...)
```

Pass `cb` as the callback to `solve!`

# Examples

```julia
julia> x_approx = solve!(solver, b) do solver, iteration
  println(iteration)
end
```
