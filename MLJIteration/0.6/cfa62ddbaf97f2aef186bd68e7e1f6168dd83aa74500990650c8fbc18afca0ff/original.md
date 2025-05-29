```
CycleLearningRate(stepsize=4, lower=0.001, upper=0.05, learning_rate_parameter=:(optimiser.η))
```

An iteration control, as in, `CycleLearningRate(learning_rate_parameter=:learning_rate)`. 

Mutate the specified `learning_rate_parameter` (defaulting to the field appropriate for MLJFlux models) to the next value in a triangular cyclic learning rate policy, using the specified `upper` and `lower` learning rate bounds. See [L. N. Smith (2019)](https://ieeexplore.ieee.org/document/7926641): "Cyclical Learning Rates for Training Neural Networks," 2017 IEEE Winter Conference on Applications of Computer Vision (WACV), Santa Rosa, CA, USA, pp. 464-472.

Here `stepsize` is half the period of the mutation cycle, measured in iterations of the underlying model. For example, `stepsize=4` means the learning rate undergoes one cycle of mutation every 8 epochs in an MLJFlux model.

**Note.** Since "one iteration" is the same as "one epoch" in MLJFlux models, this means learning rate updates can be applied once per epoch, at most, rather than "continuously" throughout an epoch as in the cited paper. 
