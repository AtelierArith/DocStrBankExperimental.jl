```
coefficients(data::AbstractMeasureData)::Vector{<:Real}
```

Return the coefficients associated with `data` associated with its expansion abstraction. This is intended as en internal method for measure creation. User-defined measure data types should extend this function if appropriate, otherwise an empty vector is returned.
