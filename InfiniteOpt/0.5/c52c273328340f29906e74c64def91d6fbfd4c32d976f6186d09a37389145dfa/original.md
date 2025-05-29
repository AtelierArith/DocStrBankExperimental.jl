```
ParameterFunctionData{F <: ParameterFunction} <: AbstractDataObject
```

A mutable `DataType` for storing `ParameterFunction`s and their data.

**Fields**

  * `func::F`: The parameter function.
  * `name::String`: The name used for printing.
  * `measure_indices::Vector{MeasureIndex}`: Indices of dependent measures.
  * `constraint_indices::Vector{InfOptConstraintIndex}`: Indices of dependent constraints.
  * `semi_infinite_var_indices::Vector{SemiInfiniteVariableIndex}`: Indices of dependent semi-infinite variables.
  * `derivative_indices::Vector{DerivativeIndex}`: Indices of dependent derivatives.
