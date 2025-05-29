```
layerwise_activations(mod::BaselineModel, queries::DataFrame)
```

Computes a forward pass of the model on the given queries and returns the layerwise activations in a `DataFrame` where activations are uniquely idendified by the `sentence_id`. If `output_hidden_states=false` was passed to `load_model` (default), only the last layer is returned. If `output_hidden_states=true` was passed to `load_model`, all layers are returned. The `layer` column indicates the layer number.

Each single activation receives its own cell to make it possible to save the output to a CSV file.
