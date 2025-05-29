```
aislogimpweights(dbm; ...)
```

Computes the logarithmised importance weights in the Annealed Importance Sampling algorithm (AIS) for estimating the ratio of the partition functions of the given DBM `dbm` to the base-rate DBM with all weights being zero and all biases equal to the biases of the `dbm`.

Implements algorithm 4 in [Salakhutdinov+Hinton, 2012]. For DBMs with Bernoulli-distributed nodes only (i. e. here DBMs of type `PartitionedBernoulliDBM`), it is possible to calculate the importance weights by summing out either the even layers (h1, h3, ...) or the odd layers (v, h2, h4, ...). In the first case, the nodes' activations in the odd layers are used to calculate the probability ratios, in the second case the even layer are used. If `dbm` is of type `PartitionedBernoulliDBM`, the optional keyword argument `sumout` can be used to choose by specifying the values `:odd` (default) or `:even`. In the case of `MultimodalDBM`s, it is not possible to choose and the second case applies there.
