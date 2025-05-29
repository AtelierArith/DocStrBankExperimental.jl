```
pad_layer(l::Layer)
```

Returns a copy of the layer `l` padded by single-qubit identity gates that act on each of the qubits not already acted upon by some gate in the layer.
