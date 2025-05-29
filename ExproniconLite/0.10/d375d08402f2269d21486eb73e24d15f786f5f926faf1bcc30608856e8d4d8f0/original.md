```
guess_type(m::Module, ex)
```

Guess the actual type of expression `ex` (of a type) in module `m`. Returns the type if it can be determined, otherwise returns the expression. This function is used in [`compare_expr`](@ref).
