```
JuMP.set_silent(model::InfiniteModel)
```

Extend `JuMP.set_silent` for infinite models to take precedence over any other attribute controlling verbosity and requires the solver to produce no output.

**Example**

```julia-repl
julia> set_silent(model)
true
```
