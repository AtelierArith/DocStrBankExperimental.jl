```
RegisteredFunction{F <: Function, G <: Union{Function, Nothing}, 
                   H <: Union{Function, Nothing}}
```

A type for storing used defined registered functions and their information that  is needed by JuMP for build an `NLPEvaluator`. The constructor is of the form:

```julia
    RegisteredFunction(name::Symbol, num_args::Int, func::Function, 
                       [gradient::Function, hessian::Function])
```

**Fields**

  * `name::Symbol`: The name of the function that is used in `NLPExpr`s.
  * `num_args::Int`: The number of function arguments.
  * `func::F`: The function itself.
  * `gradient::G`: The gradient function if one is given.
  * `hessian::H`: The hessian function if one is given.
