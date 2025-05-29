```
CheckPointSaver(filename; overwrite = false)
```

Saves checkpoints as `JLD2` files.

### Examples

```jldoctest
julia> using Optimization

julia> using OptimizationCallbacks

julia> import ForwardDiff

julia> function rosenbrock(x, p)
           (p[1] - x[1])^2 + p[2] * (x[2] - x[1]^2)^2
       end;

julia> optf = OptimizationFunction(rosenbrock, AutoForwardDiff());

julia> prob = OptimizationProblem(optf, [0., 0.], [1., 100.]);

julia> filename = tempname() * ".jld2";

julia> callback = Callback((IterationTrigger(5), EventTrigger((:end,))),
                           CheckPointSaver(filename));

julia> sol = solve(prob, Optimization.LBFGS(); callback);

julia> OptimizationCallbacks.trigger!(callback, :end);

julia> callback(Optimization.OptimizationState(u = sol.u, objective = sol.objective),
                sol.objective);

julia> using JLD2

julia> checkpoint_dict = load(filename);

julia> checkpoint_dict["15"].u
2-element Vector{Float64}:
 0.8834203727171949
 0.7694090396265355

```
