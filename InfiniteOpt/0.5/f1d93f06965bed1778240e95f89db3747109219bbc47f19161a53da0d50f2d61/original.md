```
PointVariable{I <: GeneralVariableRef} <: JuMP.AbstractVariable
```

A `DataType` for storing point variable information. Note that the elements `parameter_values` field must match the format of the parameter reference tuple defined in [`InfiniteVariable`](@ref)

**Fields**

  * `info::JuMP.VariableInfo{Float64, Float64, Float64, Float64}`: JuMP Variable information.
  * `infinite_variable_ref::I`: The infinite variable/derivative reference   associated with the point variable.
  * `parameter_values::Vector{Float64}`: The infinite parameter values   defining the point.
