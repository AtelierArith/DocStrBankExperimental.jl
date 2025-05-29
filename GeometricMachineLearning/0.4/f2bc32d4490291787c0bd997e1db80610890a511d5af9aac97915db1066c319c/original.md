```
ResNet(dim, n_blocks, activation)
```

Make an instance of a `ResNet`.

A ResNet is a neural network that realizes a mapping of the form: 

$$
    x = \mathcal{NN}(x) + x,
$$

so the input is again added to the output (a so-called add connection).  In `GeometricMachineLearning` the specific ResNet that we use consists of a series of simple [`ResNetLayer`](@ref)s.

# Constructor

`ResNet` can also be called with the constructor:

```julia
ResNet(dl, n_blocks)
```

where `dl` is an instance of `DataLoader`.

See [`iterate`](@ref) for an example of this.
