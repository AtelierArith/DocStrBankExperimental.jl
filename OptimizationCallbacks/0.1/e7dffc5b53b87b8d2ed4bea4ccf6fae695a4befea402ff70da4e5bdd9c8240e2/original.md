```
Evaluator(f; T = Float64, label = :evaluation)
```

Evaluate function `f` on `state` and store it in `evaluations`.

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

julia> callback = Callback(IterationTrigger(5), Evaluator(x -> rosenbrock(x.u, [1., 90.])));

julia> sol = solve(prob, Optimization.LBFGS(); callback);

julia> callback.func.evaluations
5-element Vector{Float64}:
 0.45989873460740843
 0.16216539624081874
 0.024525435426304077
 0.0009100921964470193
 1.0256411872737028e-13
```
