```
@constraints(model, args...)
```

Adds groups of constraints at once, in the same fashion as the [`@constraint`](@ref) macro.

The model must be the first argument, and multiple constraints can be added on multiple lines wrapped in a `begin ... end` block.

The macro returns a tuple containing the constraints that were defined.

# Examples

```julia
@constraints(model, begin
    x >= 1
    y - w <= 2
    sum_to_one[i=1:3], z[i] + y == 1
end)
```
