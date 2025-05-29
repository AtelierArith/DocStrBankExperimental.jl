```
solve!(m::abstract_mpsge_model; keywords)
Function to solve the model. Triggers the build if the model hasn't been built yet.
```

### Example

```julia-repl
julia> solve!(m, cumulative_iteration_limit=0)
```
