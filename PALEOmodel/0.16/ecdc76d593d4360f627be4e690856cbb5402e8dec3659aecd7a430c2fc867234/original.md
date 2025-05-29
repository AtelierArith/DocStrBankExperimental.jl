```
FieldRecord{FieldData <: AbstractData, Space <: AbstractSpace, V, N, Mesh <: AbstractMeshOrNothing, R}
FieldRecord(dataset, f::PB.Field, attributes; [sizehint=nothing])
```

A series of `records::R` each containing values from a `PALEOboxes.Field{FieldData, Space, N, V, Mesh}`.

Access stored values:

  * As a [`FieldArray`](@ref), using [`FieldArray(fr::FieldRecord)`](@ref) or [`get_array`](@ref).
  * For scalar data only, as a Vector using `PALEOboxes.get_data`.

# Implementation

Storage in `records::R` is an internal format that may have:

  * An optimisation to store Fields with single `values` as a Vector of `eltype(Field.values)`, cf Fields with array `values` are stored in `records` as a Vector of arrays.
  * A spatial cartesian grid stored as a linear Vector (eg `mesh` isa `PALEOboxes.Grids.CartesianLinearGrid`)
