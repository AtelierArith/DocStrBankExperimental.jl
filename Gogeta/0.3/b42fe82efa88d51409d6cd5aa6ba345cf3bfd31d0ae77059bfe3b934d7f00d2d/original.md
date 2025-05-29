```
function image_pass!(jump_model::JuMP.Model, input::Array{Float32, 4})
```

Forward pass an image through the JuMP model representing a convolutional neural network.

Returns the output of the network, i.e., a vector of the activations of the last dense layer neurons.
