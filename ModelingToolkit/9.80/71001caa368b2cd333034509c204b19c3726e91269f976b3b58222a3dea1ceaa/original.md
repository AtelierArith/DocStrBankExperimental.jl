```
discrete_events(sys::AbstractSystem) :: Vector{SymbolicDiscreteCallback}
```

Returns a vector of all the `discrete_events` in an abstract system and its component subsystems. The `SymbolicDiscreteCallback`s in the returned vector are structs with two fields: `condition` and `affect` which correspond to the first and second elements of a `Pair` used to define an event, i.e. `condition => affect`.
