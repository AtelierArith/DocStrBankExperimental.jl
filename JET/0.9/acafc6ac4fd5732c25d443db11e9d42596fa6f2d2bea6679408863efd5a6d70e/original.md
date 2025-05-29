```
@report_opt [jetconfigs...] f(args...)
```

Evaluates the arguments to a function call, determines their types, and then calls [`report_opt`](@ref) on the resulting expression.

The [general configurations](@ref) and [the optimization analysis specific configurations](@ref optanalysis-config) can be specified as an optional argument.
