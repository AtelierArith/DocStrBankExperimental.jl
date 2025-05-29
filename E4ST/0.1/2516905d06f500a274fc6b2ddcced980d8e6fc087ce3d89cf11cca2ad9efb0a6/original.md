```
get_pgen_bus(data, model, bus_idx, year_idx, hour_idx)
```

Returns total power generation for a bus at a time     * To use this to retieve the variable values after the model has been optimized, wrap the function with value() like this: value.(get*pgen*bus).
