```
sparse_group_lasso(m::Chain, α=1)
```

Get the sparse group Lasso term for sparse-input regularization, which is the combined L1 & L2 norm of the first-layer neural network weights corresponding to each input feature.

Reference: Feng & Simon, Sparse-Input Neural Networks for High-dimensional Nonparametric Regression and Classification, 2017 (pg. 4).

**Arguments:**

  * `m`: neural network model
  * `α`: (optional) Lasso (`α=0`) vs group Lasso (`α=1`) balancing parameter {0:1}

**Returns:**

  * `w_norm`: sparse group Lasso term
