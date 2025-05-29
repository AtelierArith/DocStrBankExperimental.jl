```julia
Config(
;
    threshold,
    linear_forgetting,
    draws,
    random_trials,
    prior_weight
) -> TreeParzen.Configuration.Config

```

Keyword argument outer constructor

  * `threshold::Float64`; default 0.25.
  * `linear_forgetting::Int`; default 25.`
  * `draws::Int`; default 24. `
  * `random_trials::Int`; default 20.
  * `prior_weight::Float64`; default 1.0.
