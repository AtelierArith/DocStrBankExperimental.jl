```
SemiInfiniteVariable{I <: GeneralVariableRef} <: JuMP.AbstractVariable
```

A `DataType` for storing semi-infinite variables which partially support an infinite variable.

**Fields**

  * `infinite_variable_ref::I`: The original infinite/derivvative variable.
  * `eval_supports::Dict{Int, Float64}`: The original parameter tuple linear indices                                    to the evaluation supports.
  * `parameter_nums::Vector{Int}`: The parameter numbers associated with the evaluated                                `parameter_refs`.
  * `object_nums::Vector{Int}`: The parameter object numbers associated with the                             evaluated `parameter_refs`.
