```
samplevisible(rbm, h)
samplevisible(rbm, h, factor)
```

Returns activations of the visible nodes in the AbstractRBM `rbm`, sampled from the state `h` of the hidden nodes. `h` may be a vector or a matrix that contains the samples in its rows. For the `factor`, see `visiblepotential(rbm, h, factor)`.
