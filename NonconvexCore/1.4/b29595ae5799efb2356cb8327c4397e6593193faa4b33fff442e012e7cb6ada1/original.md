```
setmax!(model::AbstractModel, max::Union{Number, AbstractVector})
setmax!(model::AbstractModel, i::Integer, max::Number)
```

Sets the variables' upper bound in `model` to `max`. Or if `i` is given, it sets the upper bound of the `i`^th variable in `model` to `max`.
