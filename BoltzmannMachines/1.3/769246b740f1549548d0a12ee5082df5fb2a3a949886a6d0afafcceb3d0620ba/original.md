```
hiddenpotential(rbm, v)
hiddenpotential(rbm, v, factor)
```

Returns the potential for activations of the hidden nodes in the AbstractRBM `rbm`, given the activations `v` of the visible nodes. `v` may be a vector or a matrix that contains the samples in its rows. The potential is a deterministic value to which sampling can be applied to get the activations. In RBMs with Bernoulli distributed hidden units, the potential of the hidden nodes is the vector of probabilities for them to be turned on.

The total input can be scaled with the `factor`. This is needed when pretraining the `rbm` as part of a DBM.
