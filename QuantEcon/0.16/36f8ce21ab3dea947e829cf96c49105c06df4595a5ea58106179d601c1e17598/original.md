```
interp(grid::AbstractVector, function_vals::AbstractVector)
```

Linear interpolation in one dimension

##### Examples

```julia
breaks = cumsum(0.1 .* rand(20))
vals = 0.1 .* sin.(breaks)
li = interp(breaks, vals)

# Do interpolation by treating `li` as a function you can pass scalars to
li(0.2)

# use broadcasting to evaluate at multiple points
li.([0.1, 0.2, 0.3])
```
