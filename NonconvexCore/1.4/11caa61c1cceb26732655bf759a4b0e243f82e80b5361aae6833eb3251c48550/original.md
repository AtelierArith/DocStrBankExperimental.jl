```
addvar!(model::AbstractModel, lb::Number, ub::Number; init = lb, integer = false)
```

Adds a new variable to `model` with lower and upper bounds `lb` and `ub`, initial value `init` and `integer = true` if the variable is integer.
