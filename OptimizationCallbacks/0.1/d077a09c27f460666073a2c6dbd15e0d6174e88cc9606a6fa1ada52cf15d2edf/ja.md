```
TimeTrigger(Δt)
```

`Δt`秒ごとにトリガーします。

### 例

```jldoctest
julia> using Optimization

julia> using OptimizationCallbacks

julia> import ForwardDiff

julia> function rosenbrock(x, p)
           sleep(.1)
           (p[1] - x[1])^2 + p[2] * (x[2] - x[1]^2)^2
       end
rosenbrock (generic function with 1 method)

julia> optf = OptimizationFunction(rosenbrock, AutoForwardDiff());

julia> prob = OptimizationProblem(optf, [0., 0.], [1., 100.]);

julia> callback = Callback(TimeTrigger(2.0), (_,_,_,_) -> @info("Hi"));

julia> sol = solve(prob, Optimization.LBFGS(); callback)
[ Info: Hi
[ Info: Hi
retcode: Success
u: 2-element Vector{Float64}:
 0.9999997057368228
 0.999999398151528

```
