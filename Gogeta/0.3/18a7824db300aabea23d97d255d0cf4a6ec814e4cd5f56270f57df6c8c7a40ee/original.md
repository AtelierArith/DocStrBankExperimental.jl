```
function image_pass!(jump_model::JuMP.Model, input::Array{Float32, 4}, cnnstruct::CNNStructure, layer::Int)
```

**Debugging version**

Forward pass an image through the JuMP model representing a convolutional neural network.

Returns the output of the layer with index given as input.
