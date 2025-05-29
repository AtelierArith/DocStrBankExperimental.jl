```
debug_system(sys::AbstractSystem; functions = [log, sqrt, (^), /, inv, asin, acos], error_nonfinite = true)
```

Wrap `functions` in `sys` so any error thrown in them shows helpful symbolic-numeric information about its input. If `error_nonfinite`, functions that output nonfinite values (like `Inf` or `NaN`) also display errors, even though the raw function itself does not throw an exception (like `1/0`). For example:

```julia-repl
julia> sys = debug_system(complete(sys))

julia> prob = ODEProblem(sys, [0.0, 2.0], (0.0, 1.0))

julia> prob.f(prob.u0, prob.p, 0.0)
ERROR: Function /(1, sin(P(t))) output non-finite value Inf with input
  1 => 1
  sin(P(t)) => 0.0
```

Additionally, all assertions in the system are optionally logged when they fail. A new parameter is also added to the system which controls whether the message associated with each assertion will be logged when the assertion fails. This parameter defaults to `true` and can be toggled by symbolic indexing with `ModelingToolkit.ASSERTION_LOG_VARIABLE`. For example, `prob.ps[ModelingToolkit.ASSERTION_LOG_VARIABLE] = false` will disable logging.
