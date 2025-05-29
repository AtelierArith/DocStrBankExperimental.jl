```
VariableAggregator(vars, cellranges, modeldata, arrays_idx) -> VariableAggregator
```

Aggregate multiple VariableDomains into a flattened list (a contiguous Vector).

Creates a `VariableAggregator` for collection of Variables `vars`, with indices from corresponding `cellranges`, for data arrays in `modeldata` with `arrays_idx`.

`cellranges` may contain `nothing` entries to indicate whole Domain.

This is mostly useful for aggregating state Variables, derivatives, etc to implement an interface to a generic ODE/DAE etc solver.

Values may be copied to and from a Vector using [`copyto!`](@ref)
