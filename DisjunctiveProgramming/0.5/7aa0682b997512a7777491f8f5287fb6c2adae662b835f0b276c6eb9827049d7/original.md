```
variable_bound_info(vref::JuMP.AbstractVariableRef)::Tuple{<:Number, <:Number}
```

Returns a tuple of the form `(lower_bound, upper_bound)` needed to implement reformulation  methods. Only works if [`requires_variable_bound_info`](@ref) is implemented.
