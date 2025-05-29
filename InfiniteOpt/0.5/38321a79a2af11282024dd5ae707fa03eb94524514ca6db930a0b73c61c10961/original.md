```
optimizer_model_expression(expr::JuMP.AbstractJuMPScalar; 
                           [label::Type{<:AbstractSupportLabel} = PublicLabel,
                           ndarray::Bool = false, 
                           kwargs...])
```

Return the reformulation expression(s) stored in the optimizer model that correspond to `expr`. Also errors if no such expression can be found in the optimizer model (meaning one or more of the underlying variables have not been transcribed).

The keyword arugments `label` and `ndarray` are what `TranscriptionOpt` employ  and `kwargs` denote extra ones that user extensions may employ in accordance with their implementation of [`optimizer_model_expression`](@ref). Errors if such an extension has not been written. 

By default only the expressions associated with public supports are returned, the  full set can be accessed via `label = All`. Moreover, infinite expressions are  returned as a list corresponding to their supports. However, a n-dimensional array  can be obtained via `ndarray = true` which is handy when the expression has multiple  infinite parameter dependencies. The corresponding supports are obtained via  `supports` using the same keyword arguments.

**Example**

```julia-repl
julia> optimizer_model_expression(my_expr) # finite expression
x(support: 1) - y
```
