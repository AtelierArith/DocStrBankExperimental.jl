```
scatter_array(sym, x::Array, workers; dim=1)::Dinfo
```

Distribute roughly equal parts of array `x` separated on dimension `dim` among `workers` into a worker-local variable `sym`.

Returns the `Dinfo` structure for the distributed data.
