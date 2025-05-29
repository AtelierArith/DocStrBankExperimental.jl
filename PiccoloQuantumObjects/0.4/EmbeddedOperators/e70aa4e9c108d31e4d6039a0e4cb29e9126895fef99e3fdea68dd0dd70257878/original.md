```
EmbeddedOperator
```

Embedded operator type to represent an operator embedded in a subspace of a larger quantum system.

# Fields

  * `operator::Matrix{ComplexF64}`: Embedded operator of size   `prod(subsystem_levels) x prod(subsystem_levels)`.
  * `subspace::Vector{Int}`: Indices of the subspace the operator is embedded in.
  * `subsystem_levels::Vector{Int}`: Levels of the subsystems in the composite system.
