```
TV <: AbstractRegularizer
```

Regularizer using the Istropic Total Variation 

# fields

  * `hyperparameter::Number`: the hyperparameter of the regularizer
  * `weight`: the weight of the regularizer, which may be used for multi-dimensional images.
  * `domain::AbstractRegularizerDomain`: the image domain where the regularization funciton will be computed.
