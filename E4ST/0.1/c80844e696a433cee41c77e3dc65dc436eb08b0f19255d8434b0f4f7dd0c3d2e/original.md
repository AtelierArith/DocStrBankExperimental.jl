```
get_pflow_bus(data, model, f_bus_idx, year_idx, hour_idx)
```

Returns net power flow out of the bus

  * To use this to retieve the variable values after the model has been optimized, wrap the function with value() like this: value.(get*pflow*bus).
