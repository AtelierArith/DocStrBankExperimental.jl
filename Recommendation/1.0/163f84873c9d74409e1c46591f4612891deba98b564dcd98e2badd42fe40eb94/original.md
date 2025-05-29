```
onehot(value, value_set::AbstractVector) -> Vector{Float64}
```

Encode a categorical value to a onehot-encoded vector. Value must be one of the elements in `value_set` in `Integer` or `String` type. `missing` or `nothing` are also acceptable as a value, but they are converted into a zero vector.
