```
LAS([T,] points; kws...)
```

Create a new `LAS` with points of type `T <: PointRecord`. The `points` can be passed as an `AbstractVector` of `PointRecord`s or as a `NamedTuple`, where the keys correspond to the point attribute names and the values are `AbstractVector`s. The keyword arguments set the corresponding fields of the `LAS` type.
