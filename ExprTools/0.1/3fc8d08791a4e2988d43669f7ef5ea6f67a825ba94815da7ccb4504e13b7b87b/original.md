```
splitdef(ex::Expr; throw::Bool=true) -> Union{Dict{Symbol,Any}, Nothing}
```

Split a function definition expression into its various components including:

  * `:head`: Expression head of the function definition (`:function`, `:(=)`, `:(->)`)
  * `:name`: Name of the function (not present for anonymous functions)
  * `:params`: Parametric types defined on constructors
  * `:args`: Positional arguments of the function
  * `:kwargs`: Keyword arguments of the function
  * `:rtype`: Return type of the function
  * `:whereparams`: Where parameters
  * `:body`: Function body (not present for empty functions)

All components listed may not be present in the returned dictionary with the exception of `:head` which will always be present.

If the provided expression is not a function then an exception will be raised when `throw=true`. Use `throw=false` avoid raising an exception and return `nothing` instead.

See also: [`combinedef`](@ref)
