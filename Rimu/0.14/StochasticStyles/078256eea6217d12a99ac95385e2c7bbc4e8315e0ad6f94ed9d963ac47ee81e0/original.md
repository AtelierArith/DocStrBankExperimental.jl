This module provides concrete implementations of [`StochasticStyle`](@ref)s, which specify the algorithm used by [`ProjectorMonteCarloProblem`](@ref Main.ProjectorMonteCarloProblem) when performing stochastic matrix-vector multiplication.

# Implemented stochastic styles:

  * [`StochasticStyle`](@ref): abstract type for stochastic styles
  * [`IsStochasticInteger`](@ref)
  * [`IsDeterministic`](@ref)
  * [`IsStochasticWithThreshold`](@ref)
  * [`IsDynamicSemistochastic`](@ref)
  * [`StyleUnknown`](@ref)

The offdiagonal spawning is defined in `spawning.jl` and is controlled by setting a [`SpawningStrategy`](@ref).

The vector compression strategies are defined in `compression.jl` and are controlled by setting a [`CompressionStrategy`](@ref).
