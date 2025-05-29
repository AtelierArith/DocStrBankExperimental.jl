```
ActivationContribution{L,C,M} <: AbstractMutableComp
ActivationContribution(l)
ActivationContribution(l, method)
```

Calculate neuron utility based on activations and gradients using `method`. 

Designed to be used as `layerfun` argument to [`fluxvertex`](@ref).

Can be a performance bottleneck in cases with large activations. Use [`NeuronUtilityEvery`](@ref) to mitigate.

Default `method` is described in [https://arxiv.org/abs/1611.06440](https://arxiv.org/abs/1611.06440).

Short summary is that the first order taylor approximation of the optimization problem: "which neurons shall I remove to minimize impact on the loss function?"  boils down to: "the ones which minimize `abs(gradient * activation)`" (assuming parameter independence).
