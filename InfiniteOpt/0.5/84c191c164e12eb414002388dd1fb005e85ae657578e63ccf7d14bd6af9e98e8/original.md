```
build_parameter_function(
    _error::Function, 
    func::Function, 
    parameter_refs::Union{GeneralVariableRef, AbstractArray{<:GeneralVariableRef}, Tuple}
    )::ParameterFunction
```

Build an [`ParameterFunction`](@ref) object that employs a parameter function  `func` that takes instances of the infinite parameter(s) as input. This can  ultimately by incorporated into expressions to enable nonlinear infinite parameter  behavior and/or incorporate data over infinite domains.

Here `func` should be of the form:

```
func(paramvals...)::Float64
```

where the formatting of `paramvals` is analagous to point variables (and will be  based on the tuple of infinite parameter references given in `parameter_refs`). 

Errors if the infinite parameter tuple is formatted incorrectly. The allowed  format follows that of infinite variables. Also errors if the function doesn't  accept a support realization of the `parameter_refs` as input.

**Example**

```julia-repl
julia> f = build_parameter_function(error, sin, t);
```
