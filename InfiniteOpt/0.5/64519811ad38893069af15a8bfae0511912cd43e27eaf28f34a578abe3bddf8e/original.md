```
JuMP.mode(model::InfiniteModel)
```

Extend `mode` to return the `MathOptInterface` mode the optimizer model is in.

**Example**

```julia-repl
julia> mode(model)
AUTOMATIC::ModelMode = 0
```
