```julia
struct Config
```

  * `threshold::Float64`
  * `linear_forgetting::Int64`
  * `draws::Int64`
  * `random_trials::Int64`
  * `prior_weight::Float64`

  * `threshold` : A value between `0` and `1`, which controls the probability threshold at   which expected improvement criteria is modeled.
  * `linear_forgetting` : A positive value which controls the number of historic points which   are used for probabilistic modelling, and older points beyond this are linearly   de-weighted.
  * `draws` : A positive value which controls the number of samples to draw when making a   recommendation for next optimisation canidate.
  * `random_trials` : A positive value which controls the number of trials of randomly   generated candidate points before TreeParzen optimisation is used.
  * `prior_weight` : A value between `0` and `1`, which controls importance of user specified   probabilistic parameters vs the history of trials.
