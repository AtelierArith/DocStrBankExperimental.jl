```
@code_mhlo [optimize = ...] [no_nan = <true/false>] f(args...)
```

Similar to `@code_hlo`, but prints the module after running the XLA compiler.

See also [`@code_xla`](@ref), [`@code_hlo`](@ref).
