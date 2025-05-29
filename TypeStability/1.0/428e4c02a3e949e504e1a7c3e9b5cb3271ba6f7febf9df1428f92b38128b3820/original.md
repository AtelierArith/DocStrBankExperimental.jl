```
check_method(func, signature, acceptable_instability=Dict())
```

Create a `StabilityReport` object describing the type stability of the method.is

Compute non-concrete types of variables and return value, returning them in a [`StabilityReport`](@ref) Object

`acceptable_instability`, if present, is a mapping of variables that are allowed be non-concrete types.  `get` is called with the mapping, the variable's symbol and `Bool` to get the variable's allowed type.  Additionally, the return value is checked using `:return` as the symbol.
