```
BayesDenoising(prior = :invgamma)
```

Regularization-based denoising using Bayesian inference for estimating the regularization parameter

**Fields**

  * `prior::Symbol`: Prior distribution over the hyperparameters used for computing the regularization parameter

      * `:invgamma`: Inverse Gamma distribution
      * `:uniform`: Uniform distribution
