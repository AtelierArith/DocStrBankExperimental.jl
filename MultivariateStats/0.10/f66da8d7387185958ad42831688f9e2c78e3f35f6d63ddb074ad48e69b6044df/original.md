```
ccacov(Cxx, Cyy, Cxy, xmean, ymean, p)
```

Compute CCA based on analysis of the given covariance matrices, using generalized eigenvalue decomposition, and return [`CCA`](@ref) model.

Parameters:

  * `Cxx`: The covariance matrix of `X`.
  * `Cyy`: The covariance matrix of `Y`.
  * `Cxy`: The covariance matrix between `X` and `Y`.
  * `xmean`: The mean vector of the **original** samples of `X`, which can be

a vector of length `dx`, or an empty vector indicating a zero mean.

  * `ymean`: The mean vector of the **original** samples of `Y`, which can be

a vector of length `dy`, or an empty vector indicating a zero mean.

  * `p`: The output dimension, *i.e* the dimension of the common space.
