```
Lion(η = 0.001, β::Tuple = (0.9, 0.999))
```

[Lion](https://arxiv.org/abs/2302.06675) optimiser.

# Parameters

  * Learning rate (`η`): Magnitude by which gradients are updating the weights.
  * Decay of momentums (`β::Tuple`): Exponential decay for the first (β1) and the                                  second (β2) momentum estimate.
