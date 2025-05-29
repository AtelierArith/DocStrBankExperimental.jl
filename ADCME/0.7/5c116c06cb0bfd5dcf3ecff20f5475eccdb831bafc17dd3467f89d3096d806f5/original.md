```
BFGS!(value_and_gradients_function::Function, initial_position::Union{PyObject, Array{Float64}}, max_iter::Int64=50, args...;kwargs...)
```

Applies the BFGS optimizer to `value_and_gradients_function`
