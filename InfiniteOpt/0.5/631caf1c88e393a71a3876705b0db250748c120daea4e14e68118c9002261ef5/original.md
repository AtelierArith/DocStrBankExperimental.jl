```
weight_function(data::AbstractMeasureData)::Function
```

Return the weight function stored in `data` associated with its expansion abstraction. This is intended as en internal method for measure creation. User-defined measure data types should extend this function if appropriate, otherwise an error is thrown.
