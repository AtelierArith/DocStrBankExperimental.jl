```
KLEntropy <: AbstractRegularizer
```

Regularizer using the Kullback-Leibler divergence (or a relative entropy).

# fields

  * `hyperparameter::Number`: the hyperparameter of the regularizer
  * `prior`: the prior image.
  * `domain::AbstractRegularizerDomain`: the image domain where the regularization funciton will be computed.   KLEntropy can be computed only in `LinearDomain()`.
