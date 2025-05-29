```
ldacov(Cp, Cn, μp, μn)
```

Performs LDA given covariances and mean vectors. Returns a linear discriminant functional of type [`LinearDiscriminant`](@ref).

*Parameters*

  * `Cp`: The covariance matrix of the positive class.
  * `Cn`: The covariance matrix of the negative class.
  * `μp`: The mean vector of the positive class.
  * `μn`: The mean vector of the negative class.

**Note:** The coefficient vector is scaled such that $\mathbf{w}'\boldsymbol{μ}_p + b = 1$ and $\mathbf{w}'\boldsymbol{μ}_n + b = -1$.
