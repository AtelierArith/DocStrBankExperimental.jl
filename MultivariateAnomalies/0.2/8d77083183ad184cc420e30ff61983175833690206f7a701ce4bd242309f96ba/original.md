```
init_MedianCycle(dat::Array{tp}, cycle_length::Int = 46)
init_MedianCycle(temporal_length::Int[, cycle_length::Int = 46])
```

initialises an init*MC object to be used as input for `get*MedianCycle!()`. Input is either some sample data or the temporal lenght of the expected input vector and the length of the annual cycle (presetting:`cycle_length = 46`)
