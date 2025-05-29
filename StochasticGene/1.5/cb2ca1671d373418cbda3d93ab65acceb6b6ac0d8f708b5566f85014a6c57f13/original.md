```
loglikelihood(param, data, model)
```

Calculates the log-likelihood for various types of data and models.

# Arguments

  * `param`: The model parameters.
  * `data`: The data, which can be of various types (e.g., `AbstractHistogramData`, `AbstractTraceData`, `TraceData`, `TraceRNAData`).
  * `model`: The model, which can be of various types (e.g., `AbstractGmodel`, `GRSMcoupledmodel`, `AbstractGRSMmodel`, `GRSMhierarchicalmodel`).

# Description

This function calculates the log-likelihood for different types of data and models. It supports histogram data, trace data, coupled models, and hierarchical models. The specific calculation method depends on the types of `data` and `model` provided.

# Methods

  * `loglikelihood(param, data::AbstractHistogramData, model::AbstractGmodel)`: Returns the log-likelihood of all data and a vector of the prediction histogram log-likelihood.
  * `loglikelihood(param, data::AbstractTraceData, model::AbstractGmodel)`: Returns the log-likelihood of combined time series traces and each trace.
  * `loglikelihood(param, data::TraceData, model::GRSMcoupledmodel)`: Returns the log-likelihood for a coupled model.
  * `loglikelihood(param, data::TraceRNAData, model::AbstractGRSMmodel)`: Returns the log-likelihood of time series traces and mRNA FISH steady state histogram.
  * `loglikelihood(param, data::AbstractTraceData, model::GRSMhierarchicalmodel)`: Returns the log-likelihood for a hierarchical model.

# Returns

  * `Float64`: The log-likelihood for the combined time series traces and each trace.
  * `Tuple{Float64, Vector{Float64}}`: The log-likelihood of all data and a vector of the prediction histogram log-likelihood.

# Convention

  * All loglikelihood functions in this codebase return the log-likelihood (higher is better), not the negative log-likelihood.
