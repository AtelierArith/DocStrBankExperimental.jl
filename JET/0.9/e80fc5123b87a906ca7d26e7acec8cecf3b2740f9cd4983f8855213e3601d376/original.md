```
report_opt(f, [types]; jetconfigs...) -> JETCallResult
report_opt(tt::Type{<:Tuple}; jetconfigs...) -> JETCallResult
report_opt(mi::Core.MethodInstance; jetconfigs...) -> JETCallResult
```

Analyzes a function call with the given type signature to detect optimization failures and unresolved method dispatches.

The [general configurations](@ref) and [the optimization analysis specific configurations](@ref optanalysis-config) can be specified as a keyword argument.

See [the documentation of the optimization analysis](@ref optanalysis) for more details.
