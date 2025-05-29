```
ConstraintData{C <: JuMP.AbstractConstraint} <: AbstractDataObject
```

A mutable `DataType` for storing constraints and their data.

**Fields**

  * `constraint::C`: The constraint.
  * `object_nums::Vector{Int}`: The object numbers of the parameter objects that the                             constraint depends on.
  * `name::String`: The name used for printing.
  * `measure_indices::Vector{MeasureIndex}`: Indices of dependent measures.
  * `is_info_constraint::Bool`: Is this is constraint based on variable info   (e.g., lower bound)
