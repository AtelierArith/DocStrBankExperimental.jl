```
FashionMNIST(; Tx=Float32, split=:train, dir=nothing)
FashionMNIST([Tx, split])
```

FashionMNIST is a dataset of Zalando's article images consisting of a training set of 60000 examples and a test set of 10000 examples. Each example is a 28x28 grayscale image, associated with a label from 10 classes. It can serve as a drop-in replacement for MNIST.

  * Authors: Han Xiao, Kashif Rasul, Roland Vollgraf
  * Website: https://github.com/zalandoresearch/fashion-mnist

See [`MNIST`](@ref) for details of the interface.
