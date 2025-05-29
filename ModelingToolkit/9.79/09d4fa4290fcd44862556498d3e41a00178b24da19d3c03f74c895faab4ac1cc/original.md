```
continuous_events(sys::AbstractSystem)::Vector{SymbolicContinuousCallback}
```

Returns a vector of all the `continuous_events` in an abstract system and its component subsystems. The `SymbolicContinuousCallback`s in the returned vector are structs with two fields: `eqs` and `affect` which correspond to the first and second elements of a `Pair` used to define an event, i.e. `eqs => affect`.
