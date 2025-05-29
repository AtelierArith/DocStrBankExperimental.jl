```
@report_call [jetconfigs...] f(args...)
```

Evaluates the arguments to a function call, determines their types, and then calls [`report_call`](@ref) on the resulting expression. This macro works in a similar way as the `@code_typed` macro.

The [general configurations](@ref) and [the error analysis specific configurations](@ref jetanalysis-config) can be specified as an optional argument.
