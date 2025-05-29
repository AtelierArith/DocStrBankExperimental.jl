```julia
MLJTreeParzenTuning(
;
    threshold,
    draws,
    linear_forgetting,
    prior_weight,
    random_trials,
    max_simultaneous_draws
) -> TreeParzen.MLJTreeParzen.MLJTreeParzenTuning

```

Keyword argument constructor

  * `threshold::Float64`; default 0.25. This is the same as `TreeParzen.Config.gamma`
  * `draws::Int`; default 24. This is the same as `TreeParzen.Config.draws`
  * `linear_forgetting::Int`; default 25. This is the same as `TreeParzen.Config.linear_forgetting`
  * `prior_weight::Float64`; default 1.0. This is the same as `TreeParzen.Config.prior_weight`
  * `random_trials::Int`; default 20. This is the same as `TreeParzen.Config.random_trials`
  * `max_simultaneous_draws::Int`; default 1. MLJ Interface specific, controls the number of   candidate hyperparameters drawn without history updates during TreeParzen optimisation   (not during suggestions/random sampling warmup), to enable MLJ parallel model training.
