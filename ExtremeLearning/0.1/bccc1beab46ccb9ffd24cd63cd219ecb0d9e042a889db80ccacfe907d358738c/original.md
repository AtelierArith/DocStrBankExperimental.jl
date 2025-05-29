```
ELM(n_hidden_neurons::Int,input_data::AbstractArray{T},output_data::AbstractArray{T}; activation::Function = sigmoid, regularization::T = zero(T)) where T<:AbstractFloat
```

Construct an ELM passing a number of neurons, the inputs and outputs. As a keyword argument, you can also pass a different activation function (Default = sigmoid). Inputs should be in the format below. | Feature1| Feature2| |––––-|––––-| |  entry1 |  entry1 | |  entry2 |  entry2 |
