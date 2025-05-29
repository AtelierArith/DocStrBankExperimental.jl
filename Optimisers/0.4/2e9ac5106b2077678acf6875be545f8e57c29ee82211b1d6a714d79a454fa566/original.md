```
Lion(η = 0.001, β = (0.9, 0.999))
Lion(; [eta, beta])
```

[Lion](https://arxiv.org/abs/2302.06675) optimiser.

# Parameters

  * Learning rate (`η == eta`): Magnitude by which gradients are updating the weights.
  * Decay of momentums (`β::Tuple == beta`): Exponential decay for the first (β1) and the                                  second (β2) momentum estimate.
