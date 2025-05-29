```
execute_function_safely(Func::Function, x::Array{T,1}; type_check::Bool = false, quiet_errors::Bool = true) where T<:Real
```

This function creates a function that executes the function for which a fixed point is sought. It is a helper function that is not exported.

### Inputs

  * `Func` - The function input to fixed_point
  * `x` - The point at which to evaluate the function.
  * `type_check` - Should the type stability of the function be checked and a error reported in an input vector of Ints turns into a vector of floats (for instance)

### Returns

  * A `FunctionEvaluationResult`

### Examples

```
Func(x) = sqrt(x)
execute_function_safely(Func, [-1.0,0.0,1.0])
execute_function_safely(Func,[Missing(),0.0,1.0])
execute_function_safely(Func,[7.0,0.0,1.0])
execute_function_safely(Func,[NaN,0.0,1.0])
execute_function_safely(Func,[Inf,0.0,1.0])
execute_function_safely(Func,-1.0)
execute_function_safely(Func,Missing())
execute_function_safely(Func,1.0)
execute_function_safely(Func,NaN)
execute_function_safely(Func,Inf)
```
