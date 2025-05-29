```
FluxNLPModel(chain_ANN data_train=MLDatasets.MNIST.traindata(Float32), data_test=MLDatasets.MNIST.testdata(Float32); size_minibatch=100)
```

Build a `FluxNLPModel` from the neural network represented by `chain_ANN`. `chain_ANN` is built using [Flux.jl](https://fluxml.ai/) for more details. The other data required are: an iterator over the training dataset `data_train`, an iterator over the test dataset `data_test` and the size of the minibatch `size_minibatch`. Suppose `(xtrn,ytrn) = Fluxnlp.data_train`
