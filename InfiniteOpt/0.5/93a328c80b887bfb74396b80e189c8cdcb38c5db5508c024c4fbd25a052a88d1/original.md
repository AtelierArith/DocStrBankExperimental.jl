```
VariableData{V <: JuMP.AbstractVariable} <: AbstractDataObject
```

A mutable `DataType` for storing variables and their data.

**Fields**

  * `variable::V`: The scalar variable.
  * `name::String`: The name used for printing.
  * `lower_bound_index::Union{InfOptConstraintIndex, Nothing}`: Index of lower bound constraint.
  * `upper_bound_index::Union{InfOptConstraintIndex, Nothing}`: Index of upper bound constraint.
  * `fix_index::Union{InfOptConstraintIndex, Nothing}`: Index on fixing constraint.
  * `zero_one_index::Union{InfOptConstraintIndex, Nothing}`: Index of binary constraint.
  * `integrality_index::Union{InfOptConstraintIndex, Nothing}`: Index of integer constraint.
  * `measure_indices::Vector{MeasureIndex}`: Indices of dependent measures.
  * `constraint_indices::Vector{InfOptConstraintIndex}`: Indices of dependent constraints.
  * `in_objective::Bool`: Is this used in objective?
  * `point_var_indices::Vector{PointVariableIndex}`: Indices of dependent point variables.
  * `semi_infinite_var_indices::Vector{SemiInfiniteVariableIndex}`: Indices of dependent semi-infinite variables.
  * `derivative_indices::Vector{DerivativeIndex}`: Indices of dependent derivatives.
  * `deriv_constr_indices::Vector{InfOptConstraintIndex}`: Indices of dependent derivative evaluation constraints.
