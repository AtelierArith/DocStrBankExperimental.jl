```
optimise_repetitions(c::AbstractCircuit, tuple_set_data::TupleSetData; options::OptimOptions = OptimOptions())
```

Returns the tuple set data after optimising the repetition numbers in the supplied tuple set data `tuple_set_data` for the circuit `c`. The optimisation is parameterised by the [`OptimOptions`](@ref) object `options`.
