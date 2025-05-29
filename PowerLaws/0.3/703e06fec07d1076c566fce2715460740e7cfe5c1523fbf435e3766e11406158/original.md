estimate_parameters

Estimate `x_min` and `α` for a given data set with respect to the [Kolmogorov-Smirnov test](https://www.encyclopediaofmath.org/index.php/Kolmogorov-Smirnov_test).

# Parameters

  * `data::AbstractArray`: Array of data which should be fit to a distribution.
  * `distribution::Type`: Distribution type, i.e. `ContinuousPowerLaw` or `DiscretePowerLaw`.
  * `xmins::AbstractArray`: If not specified, all unique values in `data` are taken as possible `x_min`s. If specified, only values in `xmins` are considered when finding the best `x_min`.
  * `xmax::Int64`: Maximum value considered in calculations. Values above `xmax` are not considered in, for example, calculating the Kolmogorov-Smirnov test.

# Returns

  * `best_fit::distribution`: A distribution of the type `distribution` fitted to the given parameters.
  * `KS::Float64`: The Kolmogorov-Smirnov distance between the data and the fitted distribution.
