```
push!(meas::TimeSeries, value)
```

`push!` an iterable many `value`s into a [`TimeSeries`] `datastream`.

# Additional Information

If the values are sufficiently long, this will trigger the `datastream` to be `resize!`d which can have `O(n)` complexity. It is preferred to  preallocate the requisite memory with [`TimeSeries`](@ref)`(name, size)`.
