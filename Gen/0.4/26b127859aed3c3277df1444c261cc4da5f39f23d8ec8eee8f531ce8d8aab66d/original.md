```
(traces, log_norm_weights, lml_est) = importance_sampling(model::GenerativeFunction,
    model_args::Tuple, observations::ChoiceMap, num_samples::Int; verbose=false)

(traces, log_norm_weights, lml_est) = importance_sampling(model::GenerativeFunction,
    model_args::Tuple, observations::ChoiceMap,
    proposal::GenerativeFunction, proposal_args::Tuple,
    num_samples::Int; verbose=false)
```

Run importance sampling, returning a vector of traces with associated log weights.

The log-weights are normalized. Also return the estimate of the marginal likelihood of the observations (`lml_est`). The observations are addresses that must be sampled by the model in the given model arguments. The first variant uses the internal proposal distribution of the model. The second variant uses a custom proposal distribution defined by the given generative function. All addresses of random choices sampled by the proposal should also be sampled by the model function. Setting `verbose=true` prints a progress message every sample.
