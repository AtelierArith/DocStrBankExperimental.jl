```
supports(data::AbstractMeasureData)::Array{Float64}
```

Return the supports associated with `data` and its infinite parameters. This is intended as en internal method for measure creation and ensures any new supports are added to parameters. User-defined measure data types should extend this function if appropriate, otherwise an empty vector is returned.
