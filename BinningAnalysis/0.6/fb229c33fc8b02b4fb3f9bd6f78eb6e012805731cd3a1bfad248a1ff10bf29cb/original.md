```
LogBinner([::Type{T}; capacity::Int])
```

Creates a `LogBinner` which can handle (at least) `capacity` many values of type `T`.

The default is `T = Float64` and `capacity = 2^32-1 ≈ 4e9`.
