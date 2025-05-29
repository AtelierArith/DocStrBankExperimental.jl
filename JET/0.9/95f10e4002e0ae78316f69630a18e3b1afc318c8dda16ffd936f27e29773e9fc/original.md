```
report_call(f, [types]; jetconfigs...) -> JETCallResult
report_call(tt::Type{<:Tuple}; jetconfigs...) -> JETCallResult
report_call(mi::Core.MethodInstance; jetconfigs...) -> JETCallResult
```

Analyzes a function call with the given type signature to find type-level errors and returns back detected problems.

The [general configurations](@ref) and [the error analysis specific configurations](@ref jetanalysis-config) can be specified as a keyword argument.

See [the documentation of the error analysis](@ref jetanalysis) for more details.
