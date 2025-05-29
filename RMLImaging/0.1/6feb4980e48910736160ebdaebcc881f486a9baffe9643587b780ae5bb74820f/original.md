```
L1Norm <: AbstractRegularizer
```

Regularizer using the l1-norm.

# fields

  * `hyperparameter::Number`: the hyperparameter of the regularizer
  * `weight`: the weight of the regularizer, which could be a number or an array.
  * `domain::AbstractRegularizerDomain`: the image domain where the regularization funciton will be computed. L1Norm can be computed only in `LinearDomain()`.
