```
MDN(; mixtures=5, layers=[128], η=1e-3, epochs=1, batchsize=32)
```

Defines an MDN model with the given hyperparameters.

# Parameters

  * `mixtures`: The number of gaussian mixtures to use in estimating the conditional distribution (default=5).
  * `layers`: A vector indicating the number of nodes in each of the hidden layers (default=[128,]).
  * `η`: The learning rate to use when training the model (default=1e-3).
  * `epochs`: The number of epochs to train the model (default=1).
  * `batchsize`: The batchsize to use during training (default=32).
