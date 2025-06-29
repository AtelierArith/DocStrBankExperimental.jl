```
module Interfaces
```

This module contains interfaces that can be used to extend and modify the algorithms and behaviours of `Rimu`.

# Interfaces

Follow the links for the definitions of the interfaces!

  * [`AbstractHamiltonian`](@ref) for defining [`Hamiltonians`](@ref Main.Hamiltonians)
  * [`AbstractOperator`](@ref) for defining observable operators
  * [`AbstractDVec`](@ref) for defining data structures for `Rimu` as in [`DictVectors`](@ref Main.DictVectors)
  * [`StochasticStyle`](@ref) for controlling the stochastic algorithms used by [`ProjectorMonteCarloProblem`](@ref Main.ProjectorMonteCarloProblem) as implemented in [`StochasticStyles`](@ref Main.StochasticStyles)

# Additional exports

## Interface functions for[`AbstractHamiltonian`](@ref)s:

  * [`diagonal_element`](@ref)
  * [`num_offdiagonals`](@ref)
  * [`get_offdiagonal`](@ref)
  * [`offdiagonals`](@ref).
  * [`random_offdiagonal`](@ref)
  * [`starting_address`](@ref)
  * [`LOStructure`](@ref)
  * [`allows_address_type`](@ref)

## working with  [`AbstractDVec`](@ref)s and [`StochasticStyle`](@ref)

  * [`deposit!`](@ref)
  * [`default_style`](@ref)
  * [`CompressionStrategy`](@ref)
  * The interface from [VectorInterface.jl](https://github.com/Jutho/VectorInterface.jl).

## Functions Rimu.jl uses to do FCIQMC:

  * [`apply_column!`](@ref)
  * [`apply_operator!`](@ref)
  * [`step_stats`](@ref)
