Stores the data matrices `X`,`Y` as well as the optimized model parameters and hyperparameters.

# Fields

  * `X::AbstractMatrix{<:Real}`: Contains the objective function inputs as columns.
  * `Y::AbstractMatrix{<:Real}`: Contains the objective function outputs as columns.
  * `params::ModelParams`: Contains MAP model (hyper)parameters.
  * `consistent::Bool`: True iff the parameters have been fitted using the current dataset (`X`, `Y`).       Is set to `consistent = false` after updating the dataset,       and to `consistent = true` after re-fitting the parameters.

See also: [`ExperimentDataBI`](@ref)
