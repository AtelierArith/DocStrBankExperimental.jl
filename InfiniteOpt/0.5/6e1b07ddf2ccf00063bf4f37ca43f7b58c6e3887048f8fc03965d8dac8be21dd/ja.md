```
optimizer_model(model::InfiniteModel)::JuMP.Model
```

`model` に格納されている JuMP モデルを返し、それを解決するために使用されます。

**例**

```julia-repl
julia> opt_model = optimizer_model(model)
A JuMP Model
Feasibility problem with:
Variables: 0
Model mode: AUTOMATIC
CachingOptimizer state: NO_OPTIMIZER
Solver name: No optimizer attached.
```
