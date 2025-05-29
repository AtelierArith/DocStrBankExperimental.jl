```
JuMP.delete(model::InfiniteModel, mref::MeasureRef)::Nothing
```

Extend `JuMP.delete` to delete measures. Errors if measure is invalid, meaning it does not belong to the model or it has already been deleted.

**Example**

```julia-repl
julia> print(model)
Min ∫{t ∈ [0, 6]}[g(t)] + z
Subject to
 z ≥ 0.0
 ∫{t ∈ [0, 6]}[g(t)] = 0
 g(t) + z ≥ 42.0, ∀ t ∈ [0, 6]
 g(0.5) = 0

julia> delete(model, meas)

julia> print(model)
Min z
Subject to
 z ≥ 0.0
 0 = 0
 g(t) + z ≥ 42.0, ∀ t ∈ [0, 6]
 g(0.5) = 0
```
