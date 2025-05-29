```
(elbo_estimate, traces, elbo_history) = black_box_vi!(
    model::GenerativeFunction, model_args::Tuple,
    [model_update::ParamUpdate,]
    observations::ChoiceMap,
    var_model::GenerativeFunction, var_model_args::Tuple,
    var_model_update::ParamUpdate;
    options...)
```

Fit the parameters of a variational model (`var_model`) to the posterior distribution implied by the given `model` and `observations` using stochastic gradient methods. Users may optionally specify a `model_update` to jointly update the parameters of `model`.

# Additional arguments:

  * `iters=1000`: Number of iterations of gradient descent.
  * `samples_per_iter=100`: Number of samples from the variational and generative       model to accumulate gradients over before a single gradient step.
  * `verbose=false`: If `true`, print information about the progress of fitting.
  * `callback`: Callback function that takes `(iter, traces, elbo_estimate)`       as input, where `iter` is the iteration number and `traces` are samples       from `var_model` for that iteration.
