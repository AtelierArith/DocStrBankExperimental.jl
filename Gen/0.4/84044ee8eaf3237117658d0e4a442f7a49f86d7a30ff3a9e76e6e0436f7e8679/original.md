```
(trace, lml_est) = importance_resampling(model::GenerativeFunction,
    model_args::Tuple, observations::ChoiceMap, num_samples::Int;
    verbose=false)

(traces, lml_est) = importance_resampling(model::GenerativeFunction,
    model_args::Tuple, observations::ChoiceMap,
    proposal::GenerativeFunction, proposal_args::Tuple,
    num_samples::Int; verbose=false)
```

Run sampling importance resampling, returning a single trace.

Unlike `importance_sampling`, the memory used constant in the number of samples.

Setting `verbose=true` prints a progress message every sample.
