```
learn!(model, strategy, data) -> model
```

Learn a `model` from `data` using `strategy`. New models/strategies/data types should overload at least one of the following:

  * [`setup!`](@ref)
  * [`update!`](@ref)
  * [`hook`](@ref)
  * [`finished`](@ref)
  * [`cleanup!`](@ref)

# `learn!` Implementation:

```
function learn!(model, s::LearningStrategy, data)
    setup!(s, model[, data])
    for (i, item) in enumerate(data)
        update!(model, s[, i], item)
        hook(s, model[, data], i)
        finished(s, model[, data], i) && break
    end
    cleanup!(s, model)
end
```
