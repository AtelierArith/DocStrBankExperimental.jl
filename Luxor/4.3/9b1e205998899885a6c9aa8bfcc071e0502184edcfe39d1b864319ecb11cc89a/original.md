```
getcells(t, a::T) where T <: AbstractArray
```

Get the Tiler/Table cells with numbers in array `a`.

Returns an array of Tuples, where each Tuple is `(Point, Number)`.
