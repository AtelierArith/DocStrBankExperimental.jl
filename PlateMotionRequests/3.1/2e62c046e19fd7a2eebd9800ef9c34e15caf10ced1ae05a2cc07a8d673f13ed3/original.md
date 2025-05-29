```
read_platemotion(file)
```

Read tab-delimited plate motion data from `file`. Expects a single tab-delimited header line, with column names that match one of the supported formats. See [`platemotion`](@ref) for details.

May throw a `PlateMotionRequests.ReadError`.
