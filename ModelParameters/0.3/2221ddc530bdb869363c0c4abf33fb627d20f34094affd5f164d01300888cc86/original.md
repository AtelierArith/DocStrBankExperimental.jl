```
Model(x)
```

A wrapper type for any model containing [`Param`](@ref) parameters - essentially marking  that a custom struct or Tuple holds `Param` fields.

This allows you to index into the model as if it is a linear list of parameters, or named  columns of values and paramiter metadata. You can treat it as an iterable, or use the  Tables.jl interface to save or update the model to/from csv, a `DataFrame` or any source  that implements the Tables.jl interface.
