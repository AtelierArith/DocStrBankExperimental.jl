```
min_num_supports(data::AbstractMeasureData)::Int
```

Return the minimum number of supports associated with `data`. By fallback, this will just return `num_supports(data)`. This is primarily intended for internal queries of `FunctionalDiscreteMeasureData`, but can be extended for other measure data types if needed.
