```julia
struct TensorBoardCallback{L, F1, F2, F3}
```

Wraps a `CoreLogging.AbstractLogger` to construct a callback to be passed to `AbstractMCMC.step`.

# Usage

```
TensorBoardCallback(; kwargs...)
TensorBoardCallback(directory::string[, stats]; kwargs...)
TensorBoardCallback(lg::AbstractLogger[, stats]; kwargs...)
```

Constructs an instance of a `TensorBoardCallback`, creating a `TBLogger` if `directory` is provided instead of `lg`.

## Arguments

  * `lg`: an instance of an `AbstractLogger` which implements `TuringCallbacks.increment_step!`.
  * `stats = nothing`: `OnlineStat` or lookup for variable name to statistic estimator. If `stats isa OnlineStat`, we will create a `DefaultDict` which copies `stats` for unseen variable names. If `isnothing`, then a `DefaultDict` with a default constructor returning a `OnlineStats.Series` estimator with `Mean()`, `Variance()`, and `KHist(num_bins)` will be used.

## Keyword arguments

  * `num_bins::Int = 100`: Number of bins to use in the histograms.
  * `filter = nothing`: Filter determining whether or not we should log stats for a particular variable and value; expected signature is `filter(varname, value)`. If `isnothing` a default-filter constructed from `exclude` and `include` will be used.
  * `exclude = String[]`: If non-empty, these variables will not be logged.
  * `include = String[]`: If non-empty, only these variables will be logged.
  * `include_extras::Bool = true`: Include extra statistics from transitions.
  * `extras_include = String[]`: If non-empty, only these extra statistics will be logged.
  * `extras_exclude = String[]`: If non-empty, these extra statistics will not be logged.
  * `extras_filter = nothing`: Filter determining whether or not we should log  extra statistics; expected signature is `filter(extra, value)`.  If `isnothing` a default-filter constructed from `extras_exclude` and  `extras_include` will be used.
  * `include_hyperparams::Bool = true`: Include hyperparameters.
  * `hyperparam_include = String[]`: If non-empty, only these hyperparameters will be logged.
  * `hyperparam_exclude = String[]`: If non-empty, these hyperparameters will not be logged.
  * `hyperparam_filter = nothing`: Filter determining whether or not we should log  hyperparameters; expected signature is `filter(hyperparam, value)`.  If `isnothing` a default-filter constructed from `hyperparam_exclude` and  `hyperparam_include` will be used.
  * `directory::String = nothing`: if specified, will together with `comment` be used to  define the logging directory.
  * `comment::String = nothing`: if specified, will together with `directory` be used to  define the logging directory.

# Fields

  * `logger::Base.CoreLogging.AbstractLogger`: Underlying logger.
  * `stats::Any`: Lookup for variable name to statistic estimate.
  * `variable_filter::Any`: Filter determining whether to include stats for a particular variable.
  * `include_extras::Bool`: Include extra statistics from transitions.
  * `extras_filter::Any`: Filter determining whether to include a particular extra statistic.
  * `include_hyperparams::Bool`: Include hyperparameters.
  * `hyperparam_filter::Any`: Filter determining whether to include a particular hyperparameter.
  * `param_prefix::String`: Prefix used for logging realizations/parameters
  * `extras_prefix::String`: Prefix used for logging extra statistics
