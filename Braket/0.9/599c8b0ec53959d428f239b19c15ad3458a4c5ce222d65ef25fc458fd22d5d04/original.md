```
QubitSet
```

An `OrderedSet`-like object which represents the qubits a [`Circuit`](@ref), [`Instruction`](@ref), or [`Result`](@ref) acts on and their ordering. Elements may be `Int`s or [`Qubit`](@ref)s.

# Examples

```jldoctest
julia> QubitSet(1, Qubit(0))
QubitSet with 2 elements:
  1
  Qubit(0)

julia> QubitSet([2, 1])
QubitSet with 2 elements:
  2
  1

julia> QubitSet()
QubitSet()

julia> QubitSet(QubitSet(5, 1))
QubitSet with 2 elements:
  5
  1
```
