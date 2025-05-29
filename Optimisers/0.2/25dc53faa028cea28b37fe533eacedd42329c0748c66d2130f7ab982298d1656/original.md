```
RMSProp(η = 1f-3, ρ = 9f-1, ϵ = eps(typeof(η)); centred = false)
```

Optimizer using the [RMSProp](https://www.cs.toronto.edu/~tijmen/csc321/slides/lecture_slides_lec6.pdf) algorithm. Often a good choice for recurrent networks. Parameters other than learning rate generally don't need tuning.

[Centred RMSProp](http://arxiv.org/abs/1308.08500) is a variant which normalises gradients by an estimate their variance, instead of their second moment.

# Parameters

  * Learning rate (`η`): Amount by which gradients are discounted before updating                      the weights.
  * Momentum (`ρ`): Controls the acceleration of gradient descent in the                 prominent direction, in effect dampening oscillations.
  * Machine epsilon (`ϵ`): Constant to prevent division by zero                        (no need to change default)
  * Keyword `centred` (or `centered`): Indicates whether to use centred variant                                    of the algorithm.
