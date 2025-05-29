```
add_bulk!(g, dep, vals)
```

Add the multiple values (`vals`) of the things identified by the keys of `vals`, with the dependency chain given by `dep`. The values of `vals` are assumed to be *equal length* vectors. Each added node will correspond to an element of the vectors. Note: The dependency chain must contain all relevant information for identifying the values.

The function returns the ids of the paths corresponding to the added values.
