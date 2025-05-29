```
num_supports(data::AbstractMeasureData)::Int
```

Return the number supports associated with `data` and its infinite parameters. This is intended as an internal method for measure creation. User-defined measure data types should extend this function if appropriate, otherwise 0 is returned.
