```
MeasureData{M <: Measure} <: AbstractDataObject
```

A mutable `DataType` for storing [`Measure`](@ref)s and their data.

**Fields**

  * `measure::M`: The measure structure.
  * `name::String`: The base name used for printing `name(meas_expr d(par))`.
  * `measure_indices::Vector{MeasureIndex}`: Indices of dependent measures.
  * `constraint_indices::Vector{InfOptConstraintIndex}`: Indices of dependent constraints.
  * `derivative_indices::Vector{DerivativeIndex}`: Indices of dependent derivatives.
  * `in_objective::Bool`: Is this used in objective?
