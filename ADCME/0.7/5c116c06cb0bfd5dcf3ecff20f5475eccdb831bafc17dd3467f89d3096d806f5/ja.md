```
BFGS!(value_and_gradients_function::Function, initial_position::Union{PyObject, Array{Float64}}, max_iter::Int64=50, args...;kwargs...)
```

`value_and_gradients_function`にBFGSオプティマイザを適用します。
