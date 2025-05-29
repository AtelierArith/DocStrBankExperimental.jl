```
laywerwise_activations(mod::BaselineModel, queries::Vector{String})
```

Computes a forward pass of the model on the given queries and returns the layerwise activations for the `HGFRobertaModel`. If `output_hidden_states=false` was passed to `load_model` (default), only the last layer is returned. If `output_hidden_states=true` was passed to `load_model`, all layers are returned. If the model is loaded with the head for classification, the activations going into the final linear layer are returned.
