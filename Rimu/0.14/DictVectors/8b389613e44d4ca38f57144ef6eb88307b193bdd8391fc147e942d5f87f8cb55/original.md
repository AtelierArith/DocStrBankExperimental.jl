Abstract supertype for projectors to be used in in lieu of DVecs or Vectors in `dot` products. Implemented subtypes:

  * [`UniformProjector`](@ref)
  * [`NormProjector`](@ref)
  * [`Norm2Projector`](@ref)
  * [`Norm1ProjectorPPop`](@ref)

See also [`PostStepStrategy`](@ref Main.PostStepStrategy) for use of projectors in [`ProjectorMonteCarloProblem`](@ref Main.ProjectorMonteCarloProblem).

## Interface

Define a method for `LinearAlgebra.dot(projector, v)`.
