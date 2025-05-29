```
OptimOptions
```

Keyword arguments for [`optimise_design`](@ref), and specifically the optimisation functions within it, including for the gradient descent function [`optimise_weights`](@ref), the repetition number optimisation function [`optimise_repetitions`](@ref), and the tuple set optimisation function [`optimise_tuple_set`](@ref).

# General options

  * `ls_type::Symbol = :gls`: Type of least squares estimator for which we optimise the design, which can be `:gls`, `:wls`, or `:ols`.
  * `est_type::Symbol = :prod`: Type of estimator for which we optimise the design, which can be `:ordinary`, `:marginal`, `:relative`, or `:sum` or `:prod`, which optimise for the arithmetic or geometric mean, respectively, of the `:ordinary` and `:relative` estimator figures of merit weighted by `est_weight`.
  * `est_weight::Real = 0.5`: Weighting of the `:ordinary` estimator figure of merit in the arithmetic or geometric mean when `est_type` is `:sum` or `:prod`, respectively, such that `:relative` is weighted by `1 - est_weight`.
  * `save_data::Bool = false`: Whether to automatically save the optimised design.

# Gradient descent options

  * `learning_rate::Real = (ls_type == :ols ? 1 : 10.0^(3/4))`: Learning rate for the gradient descent algorithm.
  * `momentum::Real = 0.99`: Momentum for the gradient descent algorithm.
  * `learning_rate_scale_factor::Real = 10.0^(1/4)`: Factor by which to reduce the learning rate if the gradient descent algorithm repeatedly steps in directions that reduce the figure of merit.
  * `max_steps::Integer = 1000`: Maximum number of gradient descent steps to take.
  * `convergence_threshold::Real = 1e-5`: Convergence threshold for the gradient descent algorithm.
  * `convergence_steps::Integer = 5`: Number of steps over which to check convergence.
  * `grad_diagnostics::Bool = false`: Whether to display gradient descent diagnostics.

# Reptition number optimisation options

  * `rep_est_type::Symbol = :relative`: Type of estimator for which we optimise the repetition number, which can be `:ordinary`, `:marginal`, `:relative`, or `:sum` or `:prod`, which optimise for the arithmetic or geometric mean, respectively, of the `:ordinary` and `:relative` estimator figures of merit weighted by `rep_est_weight`.
  * `rep_est_weight::Real = 0.5`: Weighting of the `:ordinary` estimator figure of merit in the arithmetic or geometric mean when `rep_est_type` is `:sum` or `:prod`, respectively, such that `:relative` is weighted by `1 - rep_est_weight`.
  * `error_target::Real = 0.1`: Controls initialisation of the repetition numbers, which heuristically roughly target this error rate; note that setting this to `0` initialises repetition numbers as 0, and all such repetition numbers are then set to 2 before optimisation.
  * `add_circuit::Bool = true`: Whether to add the circuit itself to the repeat tuple set.
  * `cycle_convergence_threshold::Real = 1e-5`: Convergence threshold for the cyclic coordinate descent algorithm for optimising repetition numbers.
  * `convergence_cycles::Integer = 5`: Number of steps over which to check convergence for the cyclic coordinate descent algorithm for optimising repetition numbers.
  * `min_depth::Integer = 0`: Minimum depth of repeated tuples.
  * `max_depth::Integer = 1000`: Maximum depth of repeated tuples.
  * `max_cycles::Integer = 100`: Maximum number of cycles to use in the cyclic coordinate descent algorithm for optimising repetition numbers.
  * `repeat_points::Integer = 1`: Each repeat number is augmented to have `repeat_points` repeat numbers, logarithmically spaced with the smallest repeat number which is shrunk by a factor `initial_shrink_factor`.
  * `initial_shrink_factor::Real = 2^(repeat_points - 1)`: Factor by which the smallest repeat number in an augmented tuple set is shrunk.
  * `rep_diagnostics::Bool = true`: Whether to display repetition number optimisation diagnostics.

# Tuple set optimisation options

  * `tuple_est_type::Symbol = :ordinary`: Type of estimator for which we optimise the tuple set, which can be `:ordinary`, `:marginal`, `:relative`, `:sum`, or `:prod`, which optimise for the arithmetic or geometric mean, respectively, of the `:ordinary` and `:relative` estimator figures of merit weighted by `tuple_est_weight`.
  * `tuple_est_weight::Real = 0.5`: Weighting of the `:ordinary` estimator figure of merit in the arithmetic or geometric mean when `tuple_est_type` is `:sum` or `:prod`, respectively, such that `:relative` is weighted by `1 - tuple_est_weight`.
  * `max_excursions::Integer = 100`: Number of excurisons used to optimise the tuple set.
  * `excursions_unchanged::Integer = 3`: Number of excursions that must not change the tuple set before the optimisation routine terminates.
  * `excursion_length::Integer = 5`: Number of tuples added by each excursion.
  * `extra_tuple_number::Integer = 5`: Number of tuples beyond the number in the basic tuple set added by the tuple set optimisation procedure.
  * `max_tuple_length::Integer = 20`: Maximum length of random tuples.
  * `tuple_length_zipf_power::Real = 1`: Zipf power to use when Zipf-randomly choosing the length of random tuples.
  * `repeat_zipf_powers::Vector{Float64} = [Inf; 2.0]`: Zipf power to use, chosen uniformly at random from the vector, when Zipf-randomly choosing how many times to repeat entries that will be appended to the end of a random tuple during its generation.
  * `mirror_values::Vector{Bool} = [false; true]`: Whether to mirror the tuple, chosen uniformly at random from the vector, when generating random tuples.
  * `trial_factor::Integer = 20`: Number of random tuples trialled for each tuple the excursion needs to add to the tuple set to grow it.
  * `grow_greedy::Bool = true`: Whether the excursions add tuples to the set greedily according to the figure of merit, or to add them even if this reduces the figure of merit.
  * `weight_experiments::Bool = false`: Whether to weight the shot weights for a tuple by the number of experiments for that tuple; while usually `true`, `false` performs better for tuple set optimisation.
  * `seed::Union{UInt64, Nothing} = nothing`: Seed used to randomly generate tuples.
  * `tuple_diagnostics::Bool = true`: Whether to display tuple set optimisation diagnostics.
