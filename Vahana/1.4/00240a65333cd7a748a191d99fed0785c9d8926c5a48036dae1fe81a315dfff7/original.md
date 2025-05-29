```
mapreduce(sim, f, op, ::Type{T}; [kwargs ...])
```

Calculate an aggregated value, based on the state of all agents or edges of type T.

`f` is applied to all of these agents or edges and then `op` is used to reduce (aggregate) the values returned by `f`.

mapreduce is calling Base.mapreduce, `f`, `op` and `kwargs` are passed directly to mapreduce, while `sim` and `T` are used to determine the iterator.
