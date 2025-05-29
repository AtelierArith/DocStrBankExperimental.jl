```
visiblepotential(rbm, h)
visiblepotential(rbm, h, factor)
```

Returns the potential for activations of the visible nodes in the AbstractRBM `rbm`, given the activations `h` of the hidden nodes. `h` may be a vector or a matrix that contains the samples in its rows. The potential is a deterministic value to which sampling can be applied to get the activations.

The total input can be scaled with the `factor`. This is needed when pretraining the `rbm` as part of a DBM.

In RBMs with Bernoulli distributed visible units, the potential of the visible nodes is the vector of probabilities for them to be turned on.

For a Binomial2BernoulliRBM, the visible units are sampled from a Binomial(2,p) distribution in the Gibbs steps. In this case, the potential is the vector of values for 2p. (The value is doubled to get a value in the same range as the sampled one.)

For GaussianBernoulliRBMs, the potential of the visible nodes is the vector of means of the Gaussian distributions for each node.
