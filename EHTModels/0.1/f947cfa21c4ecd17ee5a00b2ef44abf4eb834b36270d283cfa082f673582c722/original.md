```
visibility_point(model::AbstractModel, u, v, args...)
```

Function that computes the pointwise visibility. This must be implemented in the model interface if `visanalytic(::Type{MyModel}) == IsAnalytic()`
