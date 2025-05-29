```
project(data::DataMatrix, model::ProjectionModel, args...; verbose=true, kwargs...)
```

Core projection function. Project `data` based on the single `ProjectionModel` `model`. In most cases, it is better to call `project(data, base::DataMatrix)` instead of using this method directly.
