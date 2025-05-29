```
MultiParameterData{P <: DependentParameters} <: AbstractDataObject
```

A mutable `DataType` for storing [`DependentParameters`](@ref) and their data.

**Fields**

  * `parameters::P`: The parameter collection.
  * `object_num::Int`: The location of the corresponding `ObjectIndex` in  `InfiniteModel.param_object_indices` (given by `InfiniteModel.last_object_num`).
  * `parameter_nums::UnitRange{Int}`: Given by `InfiniteModel.last_param_num`                                   (updated when prior parameters are deleted)
  * `names::Vector{String}`: The names used for printing each parameter.
  * `parameter_func_indices::Vector{ParameterFunctionIndex}`: Indices of  dependent infinite parameter functions.
  * `infinite_var_indices::Vector{InfiniteVariableIndex}`: Indices of  dependent infinite variables.
  * `derivative_indices::Vector{Vector{DerivativeIndex}}`: Indices of dependent derivatives.
  * `measure_indices::Vector{Vector{MeasureIndex}}`: Indices of dependent measures.
  * `constraint_indices::Vector{Vector{InfOptConstraintIndex}}`: Indices of dependent constraints.
  * `has_internal_supports::Bool`: Does this parameter have internal supports?
  * `has_deriv_constrs::Bool`: Have any derivative evaluation constraints been added                             to the infinite model associated with this parameter?
