```
TripolarGrid(arch::Distributed, FT::DataType = Float64; halo = (4, 4, 4), kwargs...)
```

Construct a tripolar grid on a distributed architecture. A distributed tripolar grid is supported only on a Y-partitioning configuration, therefore, only splitting the j-direction is supported for the moment.
