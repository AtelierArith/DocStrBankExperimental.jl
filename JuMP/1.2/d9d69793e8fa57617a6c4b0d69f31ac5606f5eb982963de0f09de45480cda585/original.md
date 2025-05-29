```
parse_constraint_call(
    _error::Function,
    is_vectorized::Bool,
    ::Val{op},
    args...,
)
```

Implement this method to intercept the parsing of a `:call` expression with operator `op`.

!!! warning
    Extending the constraint macro at parse time is an advanced operation and has the potential to interfere with existing JuMP syntax. Please discuss with the [developer chatroom](https://gitter.im/JuliaOpt/jump-dev) before publishing any code that implements these methods.


## Arguments

  * `_error`: a function that accepts a `String` and throws the string as an error, along with some descriptive information of the macro from which it was thrown.
  * `is_vectorized`: a boolean to indicate if `op` should be broadcast or not
  * `op`: the first element of the `.args` field of the `Expr` to intercept
  * `args...`: the `.args` field of the `Expr`.

## Returns

This function must return:

  * `parse_code::Expr`: an expression containing any setup or rewriting code that needs to be called before `build_constraint`
  * `build_code::Expr`: an expression that calls `build_constraint(` or `build_constraint.(` depending on `is_vectorized`.

See also: [`parse_constraint_head`](@ref), [`build_constraint`](@ref)
