```
optimise_design(c::AbstractCircuit; options::OptimOptions = OptimOptions())
optimise_design(c::AbstractCircuit, tuple_set_data::TupleSetData; options::OptimOptions = OptimOptions())
```

Returns an optimised experimental design for the circuit `c` initialised with the tuple set data `tuple_set_data`. The optimisation is parameterised by the [`OptimOptions`](@ref) object `options`.
