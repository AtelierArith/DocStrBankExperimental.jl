```
setmin!(model::AbstractModel, min::Union{Number, AbstractVector})
setmin!(model::AbstractModel, i::Integer, min::Number)
```

Sets the variables' lower bounds in `model` to `min`. Or if `i` is given, it sets the lower bound of the `i`^th variable in `model` to `min`.
