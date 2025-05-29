```julia
fmin(
    fn::Function,
    space::Union{TreeParzen.Types.AbstractDelayed, Dict{Symbol}, AbstractVector},
    N::Int64,
    points::Vector{TreeParzen.Trials.Trial};
    threshold,
    linear_forgetting,
    draws,
    random_trials,
    prior_weight,
    logging_interval
) -> Any

```

Find the set of hyperparameters that return the lowest value from the submitted function.

# Arguments

  * `fn` : The function that you want to evaluate. Note that the function needs to accept a   single `Dict` and return a `Float64`. If your function does not accept a `Dict` you will   need to create a wrapping function that translates the content of the `Dict` to the   parameters your function needs. Similarly if you want to maximise your function instead   of minimise it, your wrapping function will need to invert the output.   See the TreeParzen user guide for examples.
  * `space` : A `Dict` containing objects from the `TreeParzen.HP` module that describe the   space of hyperparameters that TreeParzen is allowed to search.
  * `N` : Number of trials to perform.
  * `points` : A list of trials chosen by the user to be evaluated before optimisation. The   list can be empty. Example:       `[Dict(:x => 0.0, :y => 0.0), Dict(:x => 1.0, :y => 2.0)]`

## Optional keyword arguments

  * `threshold::Float64` : A value between `0` and `1`, which controls the probability threshold at   which expected improvement criteria is modeled.
  * `linear_forgetting::Int` : A positive value which controls the number of historic points which   are used for probabilistic modelling, and older points beyond this are linearly   de-weighted.
  * `draws::Int` : A positive value which controls the number of samples to draw when making a   recommendation for next optimisation candidate.
  * `random_trials::Int` : A positive value which controls the number of trials of randomly   generated candidate points before TreeParzen optimisation is used.
  * `prior_weight::Float64` : A value between `0` and `1`, which controls importance of user specified   probabilistic parameters vs the history of trials.
  * `logging_interval::Int` : An integer specifying after how many iterations should a progress   statement be logged out. Default, -1, will log only upon completion.
