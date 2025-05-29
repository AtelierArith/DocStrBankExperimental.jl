```
evaloutput(model::SimModel, d=[]) -> y
```

Evaluate `SimModel` outputs `y` from `model.x0` states and measured disturbances `d`.

It returns `model` output at the current time step $\mathbf{y}(k)$. Calling a  [`SimModel`](@ref) object calls this `evaloutput` method.

# Examples

```jldoctest
julia> model = setop!(LinModel(tf(2, [10, 1]), 5.0), yop=[20]);

julia> y = evaloutput(model)
1-element Vector{Float64}:
 20.0
```
