```
promote_cols!(data)
```

promotes columns of every table in data to be `Vector{CT}` for all `Vector{AT}` where `AT` is an abstract type and every element is of concrete type `CT`
