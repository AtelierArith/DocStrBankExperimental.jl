Main module for `JunctionTrees.jl` – a Julia implementation of the junction tree algorithm.

One main function is exported from this module for public use:

  * [`compile_algo`](@ref). Compiles and returns an expression that computes the posterior marginals of the model given evidence using the junction tree algorithm.

# Exports

  * [`BackwardPass`](@ref)
  * [`Factor`](@ref)
  * [`ForwardPass`](@ref)
  * [`JointMarginals`](@ref)
  * [`LastStage`](@ref)
  * [`Marginals`](@ref)
  * [`UnnormalizedMarginals`](@ref)
  * [`compile_algo`](@ref)
  * [`norm`](@ref)
  * [`prod`](@ref)
  * [`redu`](@ref)
  * [`sum`](@ref)
