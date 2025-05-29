```
ParameterFunction{F <: Function, VT <: VectorTuple}
```

A `DataType` for storing known functions of infinite parameters. These equate to arbitrary  functions that take support instances of infinite parameters `parameter_refs` in  as input and compute a scalar value as output via `func`. These can then can  incorporated in expressions via [`ParameterFunctionRef`](@ref)s.

**Fields**

  * `func::F`: The function the takes infinite parameters as input and provide a            scalar number as output.
  * `parameter_refs::VT`: The infinite parameter references that serve as                                   inputs to `func`. Their formatting is analagous                                   to those of infinite variables.
  * `parameter_nums::Vector{Int}`: The parameter numbers of `parameter_refs`.
  * `object_nums::Vector{Int}`: The parameter object numbers associated with `parameter_refs`.
