```
updatestate!(model::SimModel, u, d=[]) -> xnext
```

Update `model.x0` states with current inputs `u` and meas. dist. `d` for the next time step.

The method computes and returns the model state for the next time step $\mathbf{x}(k+1)$.

# Examples

```jldoctest
julia> model = LinModel(ss(1.0, 1.0, 1.0, 0, 1.0));

julia> x = updatestate!(model, [1])
1-element Vector{Float64}:
 1.0
```
