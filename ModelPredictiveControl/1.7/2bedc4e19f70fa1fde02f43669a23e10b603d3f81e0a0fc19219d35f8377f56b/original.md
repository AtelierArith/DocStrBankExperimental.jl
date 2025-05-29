```
initstate!(model::SimModel, u, d=[]) -> x
```

Init `model.x0` with manipulated inputs `u` and meas. dist. `d` steady-state.

The method tries to initialize the model state $\mathbf{x}$ at steady-state. It removes the operating points on `u` and `d` and calls [`steadystate!`](@ref):

  * If `model` is a [`LinModel`](@ref), the method computes the steady-state of current inputs `u` and measured disturbances `d`.
  * Else, `model.x0` is left unchanged. Use [`setstate!`](@ref) to manually modify it.

# Examples

```jldoctest
julia> model = LinModel(tf(6, [10, 1]), 2.0);

julia> u = [1]; x = initstate!(model, u); y = round.(evaloutput(model), digits=3)
1-element Vector{Float64}:
 6.0
 
julia> x ≈ updatestate!(model, u)
true
```
