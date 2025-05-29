```
struct QuEraTaskSpecification <: QuEraSchema
```

The schema representation of a task for the machine.

Is the output of [`to_schema`](@ref) and [`to_schema_no_validation`](@ref) as well as input to [`execute(task::QuEraTaskSpecification)`](@ref).

# Fields

  * `nshots::Int`: Number of shots (number of times hamiltonian is executed)
  * `lattice::Lattice`: The Bravais lattice vectors and sites
  * `effective_hamiltonian::EffectiveHamiltonian`: a `RydbergHamiltonian` instance

wrapped inside an `EffectiveHamiltonian`
