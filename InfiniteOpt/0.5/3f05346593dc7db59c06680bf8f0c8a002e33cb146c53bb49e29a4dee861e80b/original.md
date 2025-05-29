```
InfiniteVariable{F <: Function, VT <: VectorTuple} <: JuMP.AbstractVariable
```

A `DataType` for storing core infinite variable information. Note that indices that refer to the same dependent parameter group must be in the same tuple element. It is important to note that `info.start` should contain a start value function that generates the start value for a given infinite parameter support. This function should map a support to a start value using user-formatting if `is_vector_start = false`, otherwise it should do the mapping using a single support vector as input.

**Fields**

  * `info::JuMP.VariableInfo{Float64, Float64, Float64, F}`: JuMP variable information. Here the start value is a function that maps the parameter values to a start value.
  * `parameter_refs::VT`: The infinite parameter references that parameterize the  variable.
  * `parameter_nums::Vector{Int}`: The parameter numbers of `parameter_refs`.
  * `object_nums::Vector{Int}`: The parameter object numbers associated with `parameter_refs`.
  * `is_vector_start::Bool`: Does the start function take support values formatted as vectors?
