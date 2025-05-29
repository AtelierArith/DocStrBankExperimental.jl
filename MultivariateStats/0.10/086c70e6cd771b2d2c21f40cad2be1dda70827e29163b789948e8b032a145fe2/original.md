```
ldacov(C, μp, μn)
```

Performs LDA given a covariance matrix `C` and both mean vectors `μp` & `μn`.  Returns a linear discriminant functional of type [`LinearDiscriminant`](@ref).

*Parameters*

  * `C`: The pooled covariance matrix (*i.e* $(\mathbf{C}_p + \mathbf{C}_n)/2$)
  * `μp`: The mean vector of the positive class.
  * `μn`: The mean vector of the negative class.
