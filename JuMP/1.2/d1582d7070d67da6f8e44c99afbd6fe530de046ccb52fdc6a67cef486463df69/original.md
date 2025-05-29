```
parse_constraint_head(_error::Function, ::Val{head}, args...)
```

Implement this method to intercept the parsing of an expression with head `head`.

!!! warning
    Extending the constraint macro at parse time is an advanced operation and has the potential to interfere with existing JuMP syntax. Please discuss with the [developer chatroom](https://gitter.im/JuliaOpt/jump-dev) before publishing any code that implements these methods.


## Arguments

  * `_error`: a function that accepts a `String` and throws the string as an error, along with some descriptive information of the macro from which it was thrown.
  * `head`: the `.head` field of the `Expr` to intercept
  * `args...`: the `.args` field of the `Expr`.

## Returns

This function must return:

  * `is_vectorized::Bool`: whether the expression represents a broadcasted expression like `x .<= 1`
  * `parse_code::Expr`: an expression containing any setup or rewriting code that needs to be called before `build_constraint`
  * `build_code::Expr`: an expression that calls `build_constraint(` or `build_constraint.(` depending on `is_vectorized`.

## Existing implementations

JuMP currently implements:

  * `::Val{:call}`, which forwards calls to [`parse_constraint_call`](@ref)
  * `::Val{:comparison}`, which handles the special case of `l <= body <= u`.

See also: [`parse_constraint_call`](@ref), [`build_constraint`](@ref)
