```
samplehidden(rbm, v)
samplehidden(rbm, v, factor)
```

Returns activations of the hidden nodes in the AbstractRBM `rbm`, sampled from the state `v` of the visible nodes. `v` may be a vector or a matrix that contains the samples in its rows. For the `factor`, see `hiddenpotential(rbm, v, factor)`.
