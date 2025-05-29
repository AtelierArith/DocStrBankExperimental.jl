```
value(rs::AbstractReservoirSample)
```

Returns the elements collected in the sample at the current  sampling stage.

Note that even if the sampling respects the schema it is assigned when [`ReservoirSample`](@ref) is instantiated, some ordering in  the sample can be more probable than others. To represent each one  with the same probability call `shuffle!` over the result.
