```
ScalarParameterData{P <: ScalarParameter} <: AbstractDataObject
```

A mutable `DataType` for storing `ScalarParameter`s and their data.

**Fields**

  * `parameter::P`: The scalar parameter.
  * `object_num::Int`: The location of the corresponding `ObjectIndex` in   `InfiniteModel.param_object_indices` (given by `InfiniteModel.last_object_num`).
  * `parameter_num::Int`: Given by `InfiniteModel.last_param_num` (updated when                       prior parameters are deleted)
  * `name::String`: The name used for printing.
  * `parameter_func_indices::Vector{ParameterFunctionIndex}`: Indices of dependent  infinite parameter functions.
  * `infinite_var_indices::Vector{InfiniteVariableIndex}`: Indices of dependent  infinite variables.
  * `derivative_indices::Vector{DerivativeIndex}`: Indices of dependent derivatives.
  * `measure_indices::Vector{MeasureIndex}`: Indices of dependent measures.
  * `constraint_indices::Vector{InfOptConstraintIndex}`: Indices of dependent constraints.
  * `in_objective::Bool`: Is this used in objective? This should be true only for finite parameters.
  * `generative_measures::Vector{MeasureIndex}`: Indices of measures that use `parameter.generative_supp_info`.
  * `has_internal_supports::Bool`: Does this parameter have internal supports?
  * `has_generative_supports::Bool`: Have any generative supports been added?
  * `has_deriv_constrs::Bool`: Have any derivative evaluation constraints been added                             to the infinite model associated with this parameter?
