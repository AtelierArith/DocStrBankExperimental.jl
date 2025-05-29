```
predict(mix::MixtureModel, y::AbstractVector; robust=false)
```

Evaluate the most likely category for each observations given a `MixtureModel`.

  * `robust = true` will prevent the (log)likelihood to overflow to `-∞` or `∞`.
