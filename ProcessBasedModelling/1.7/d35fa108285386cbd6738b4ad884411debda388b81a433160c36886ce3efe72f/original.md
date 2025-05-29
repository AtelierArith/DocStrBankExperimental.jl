```
Process
```

A new process must subtype `Process` and can be used in [`processes_to_mtkmodel`](@ref). The type must extend the following functions from the module `ProcessBasedModelling`:

  * `lhs_variable(p)` which returns the variable the process describes (left-hand-side variable). There is a default implementation `lhs_variable(p) = p.variable` if the field exists.
  * `rhs(p)` which is the right-hand-side expression, i.e., the "actual" process.
  * (optional) `timescale(p)`, which defaults to [`NoTimeDerivative`](@ref).
  * (optional) `lhs(p)` which returns the left-hand-side. Let `τ = timescale(p)`. Then default `lhs(p)` behaviour depends on `τ` as follows:

      * Just `lhs_variable(p)` if `τ == NoTimeDerivative()`.
      * `Differential(t)(p)` if `τ == nothing`, or multiplied with a number if `τ isa LiteralParameter`.
      * `τ_var*Differential(t)(p)` if `τ isa Union{Real, Num}`. If real, a new named parameter `τ_var` is created that has the prefix `:τ_` and then the lhs-variable name and has default value `τ`. Else if `Num`, `τ_var = τ` as given.
      * Explicitly extend `lhs_variable` if the above do not suit you.
