```
ParameterProcess(variable, value = default_value(variable)) <: Process
```

The simplest process which equates a given `variable` to a constant value that is encapsulated in a parameter. If `value isa Real`, then a named parameter with the name of `variable` and `_0` appended is created. Else, if `valua isa Num` then it is taken as the paremeter directly.

Example:

```julia
@variables T(t) = 0.5
proc = ParameterProcess(T)
```

will create the equation `T ~ T_0`, where `T_0` is a `@parameter` with default value `0.5`.
