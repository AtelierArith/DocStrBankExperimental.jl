```
rand!([rng::AbstractRNG,] s::Sampleable, A::AbstractArray)
```

Generate one or multiple samples from `s` to a pre-allocated array `A`. `A` should be in the form as specified above. The rules are summarized as below:

  * When `s` is univariate, `A` can be an array of arbitrary shape. Each element of `A` will be overridden by one sample.
  * When `s` is multivariate, `A` can be a vector to store one sample, or a matrix with each column for a sample.
  * When `s` is matrix-variate, `A` can be a matrix to store one sample, or an array of matrices with each element for a sample matrix.
