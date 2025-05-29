```
reformulate_model(model::JuMP.AbstractModel, method::AbstractSolutionMethod = BigM())
```

Reformulate a `GDPModel` using the specified `method`. Prior to reformulation, all previous reformulation variables and constraints are deleted.
