```
function get_structure(CNN_model::Flux.Chain, input::Array{Float32, 4})
```

Extract the layer structure of a convolutional neural network. The input image is needed to calculate the correct sizes for the hidden 2-dimensional layers.

Returns a `CNNStructure` struct.
