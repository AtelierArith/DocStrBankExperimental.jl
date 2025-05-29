```
ProdCVI
```

The `ProdCVI` structure defines the approximation method hyperparameters of the `prod(approximation::CVI, logp::F, dist)`. This method performs an approximation of the product of the `dist` and `logp` with Stochastic Variational message passing (SVMP-CVI) (See [`Probabilistic programming with stochastic variational message passing`](https://biaslab.github.io/publication/probabilistic_programming_with_stochastic_variational_message_passing/)).

!!! note
    `ProdCVI` is deprecated in favor of `CVIProjection`.


Arguments

  * `rng`: random number generator
  * `n_samples`: number of samples to use for statistics approximation
  * `n_iterations`: number of iteration for the natural parameters gradient optimization
  * `opt`: optimizer, which will be used to perform the natural parameters gradient optimization step
  * `grad`: optional, defaults to `ForwardDiffGrad()`, structure to select how the gradient and the hessian will be computed
  * `n_gradpoints`: optional, defaults to 1, number of points to estimate gradient of the likelihood (dist*logp)
  * `enforce_proper_messages`: optional, defaults to true, ensures that a message, computed towards the inbound edges, is a proper distribution, must be of type `Val(true)/Val(false)`
  * `warn`: optional, defaults to true, enables or disables warnings related to the optimization steps

!!! note
    `n_gradpoints` option is ignored in the Gaussian case


!!! note
    Adding the `Optimisers.jl` in your Julia environment enables additional optimizers from the `Optimisers.jl` for the CVI approximation method. Adding the `DiffResults` in your Julia environment enables faster gradient computations in case if all inputs are of the `Gaussian` type.

