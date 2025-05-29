```
struct AccumulatingEmissions <: Accumulating
```

`StorageBehavior` which accumulates all inflow witin a strategic period. `AccumulatingEmissions` allows as well to serve as a [`ResourceEmit`](@ref) emission point to represent a soft constraint on storing the captured emissions.
