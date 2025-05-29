```
boxconstraints(lb, ub, [rigid])
BoxConstrainedSpace(ub, lb, [rigid])
```

Define a box-constrained search space (alias for BoxConstrainedSpace).

See [`SearchSpaces.BoxConstrainedSpace`](@ref) for more details.

# Example

```julia
f(x) = (x[1] - 100)^2 + sum(abs.(x[2:end]))
bounds = boxconstraints(lb = zeros(5), ub = ones(5), rigid = false)
optimize(f, bounds, ECA)
```
