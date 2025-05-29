```
struct CNNStructure
```

Container for the layer structure of a convolutional neural network.

This structure is used for passing the CNN parameters from one function to another. This structure can be created with the `get_structure` -function.

# Fields

  * `channels`: dictionary of (layer, number of channels) pairs for convolutional or pooling layers
  * `dims`: dictionary of (layer, (# of rows, # of columns)) pairs for convolutional or pooling layers
  * `dense_lengths`: dictionary of (layer, # of neurons) pairs for dense and flatten layers
  * `conv_inds`: vector of the convolutional layer indices
  * `maxpool_inds_inds`: vector of the maxpool layer indices
  * `meanpool_inds`: vector of the meanpool layer indices
  * `flatten_ind`: index of the `Flux.flatten` layer
  * `dense_inds`: vector of the dense layer indices

```
