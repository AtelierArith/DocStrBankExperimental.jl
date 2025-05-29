```
dense(inputs::Union{PyObject, Array{<:Real}}, units::Int64, args...; 
    activation::Union{String, Function} = nothing, kwargs...)
```

Creates a fully connected layer with the activation function specified by `activation`
