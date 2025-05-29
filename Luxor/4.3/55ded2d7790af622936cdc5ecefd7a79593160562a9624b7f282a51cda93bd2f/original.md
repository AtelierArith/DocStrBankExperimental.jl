```
getcells(t, n::T) where T <: AbstractRange
```

Get the Tiler/Table cells with numbers in range `n`.

Returns an array of Tuples, where each Tuple is `(Point, Number)`.
