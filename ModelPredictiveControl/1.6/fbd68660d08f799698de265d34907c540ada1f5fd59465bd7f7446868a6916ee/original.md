```
linearize!(linmodel::LinModel, model::SimModel; <keyword arguments>) -> linmodel
```

Linearize `model` and store the result in `linmodel` (in-place).

The keyword arguments are identical to [`linearize`](@ref). The code is allocation-free if `model` simulations does not allocate.

# Examples

```jldoctest
julia> model = NonLinModel((x,u,_,_)->x.^3 + u, (x,_,_)->x, 0.1, 1, 1, 1, solver=nothing);

julia> linmodel = linearize(model, x=[10.0], u=[0.0]); linmodel.A
1×1 Matrix{Float64}:
 300.0

julia> linearize!(linmodel, model, x=[20.0], u=[0.0]); linmodel.A
1×1 Matrix{Float64}:
 1200.0
```
