```
from_namedtuple(posterior::NamedTuple; kwargs...) -> InferenceData
from_namedtuple(posterior::Vector{Vector{<:NamedTuple}}; kwargs...) -> InferenceData
from_namedtuple(
    posterior::NamedTuple,
    sample_stats::Any,
    posterior_predictive::Any,
    predictions::Any,
    log_likelihood::Any;
    kwargs...
) -> InferenceData
```

Convert a `NamedTuple` or container of `NamedTuple`s to an `InferenceData`.

If containers are passed, they are flattened into a single `NamedTuple` with array elements whose first dimensions correspond to the dimensions of the containers.

# Arguments

  * `posterior`: The data to be converted. It may be of the following types:

      * `::NamedTuple`: The keys are the variable names and the values are arrays with dimensions `(ndraws, nchains[, sizes...])`.
      * `::Vector{Vector{<:NamedTuple}}`: A vector of length `nchains` whose elements have length `ndraws`.

# Keywords

  * `posterior_predictive::Any=nothing`: Draws from the posterior predictive distribution
  * `sample_stats::Any=nothing`: Statistics of the posterior sampling process
  * `predictions::Any=nothing`: Out-of-sample predictions for the posterior.
  * `prior=nothing`: Draws from the prior. Accepts the same types as `posterior`.
  * `prior_predictive::Any=nothing`: Draws from the prior predictive distribution
  * `sample_stats_prior::Any=nothing`: Statistics of the prior sampling process
  * `observed_data::NamedTuple`: Observed data on which the `posterior` is conditional. It should only contain data which is modeled as a random variable. Keys are parameter names and values.
  * `constant_data::NamedTuple`: Model constants, data included in the model which is not modeled as a random variable. Keys are parameter names and values.
  * `predictions_constant_data::NamedTuple`: Constants relevant to the model predictions (i.e. new `x` values in a linear regression).
  * `log_likelihood`: Pointwise log-likelihood for the data. It is recommended to use this argument as a `NamedTuple` whose keys are observed variable names and whose values are log likelihood arrays.
  * `library`: Name of library that generated the draws
  * `coords`: Map from named dimension to named indices
  * `dims`: Map from variable name to names of its dimensions

# Returns

  * `InferenceData`: The data with groups corresponding to the provided data

!!! note
    If a `NamedTuple` is provided for `observed_data`, `constant_data`, or predictions*constant*data`, any non-array values (e.g. integers) are converted to 0-dimensional arrays.


# Examples

```@example
using InferenceObjects
nchains = 2
ndraws = 100

data1 = (
    x=rand(ndraws, nchains), y=randn(ndraws, nchains, 2), z=randn(ndraws, nchains, 3, 2)
)
idata1 = from_namedtuple(data1)

data2 = [[(x=rand(), y=randn(2), z=randn(3, 2)) for _ in 1:ndraws] for _ in 1:nchains];
idata2 = from_namedtuple(data2)
```
