```
Callback(trigger, function; t = 0, extra = nothing, stop = (_, _, _, _) -> false)

Callback((trigger1, trigger2, ...), function)
```

See triggers [`IterationTrigger`](@ref), [`TimeTrigger`](@ref), [`EventTrigger`](@ref). For callback functions see [`LogProgress`](@ref), [`CheckPointSaver`](@ref).

The callback `function` has arguments `Optimization.OptimizationState, value, t, extra`.

### Example

```jldoctest
julia> using Optimization

julia> using OptimizationCallbacks

julia> import ForwardDiff

julia> function rosenbrock(x, p)
           (p[1] - x[1])^2 + p[2] * (x[2] - x[1]^2)^2
       end
rosenbrock (generic function with 1 method)

julia> optf = OptimizationFunction(rosenbrock, AutoForwardDiff());

julia> prob = OptimizationProblem(optf, [0., 0.], [1., 100.]);

julia> callback = Callback(IterationTrigger(5), LogProgress());

julia> sol = solve(prob, Optimization.LBFGS(); callback)
 eval   | current     | lowest      | highest
_________________________________________________
      5 |    0.460215 |    0.460215 |    0.460215
     10 |    0.162607 |    0.162607 |    0.460215
     15 |   0.0257404 |   0.0257404 |    0.460215
     20 | 0.000911646 | 0.000911646 |    0.460215
     25 | 1.04339e-13 | 1.04339e-13 |    0.460215
retcode: Success
u: 2-element Vector{Float64}:
 0.9999997057368228
 0.999999398151528

```
