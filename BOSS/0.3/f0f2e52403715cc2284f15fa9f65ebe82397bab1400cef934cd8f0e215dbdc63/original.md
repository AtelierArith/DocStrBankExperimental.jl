An abstract type for a fitness function measuring the quality of an output `y` of the objective function.

Fitness is used by the `AcquisitionFunction` to determine promising points for future evaluations.

All fitness functions *should* implement:

  * (::CustomFitness)(y::AbstractVector{<:Real}) -> fitness::Real

An exception is the `NoFitness`, which can be used for problem without a well defined fitness. In such case, an `AcquisitionFunction` which does not depend on `Fitness` must be used.

See also: [`NoFitness`](@ref), [`LinFitness`](@ref), [`NonlinFitness`](@ref), [`AcquisitionFunction`](@ref)
