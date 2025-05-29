```
ae(x::PyObject, output_dims::Array{Int64}, scope::String = "default";
    activation::Union{Function,String} = "tanh")
```

Alias: `fc`, `ae`

Creates a neural network with intermediate numbers of neurons `output_dims`.
