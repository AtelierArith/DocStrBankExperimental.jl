```
coefficient_function(data::AbstractMeasureData)::Function
```

Return the coefficient function stored in `data` associated with its expansion abstraction is there is such a function. This is intended as an internal method for measure creation. User-defined measure data types should extend this function if appropriate, otherwise an error is thrown for unsupported types.
