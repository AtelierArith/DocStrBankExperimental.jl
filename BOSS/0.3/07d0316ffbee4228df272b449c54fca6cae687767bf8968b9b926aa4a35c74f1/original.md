Stores the initial data.

At least one initial datapoint has to be provided (purely for implementation reasons). One can for example use LatinHypercubeSampling.jl to obtain a small intial grid, or provide a single random initial datapoint.

# Fields

  * `X::AbstractMatrix{<:Real}`: Contains the objective function inputs as columns.
  * `Y::AbstractMatrix{<:Real}`: Contains the objective function outputs as columns.

See also: [`ExperimentDataPost`](@ref)
