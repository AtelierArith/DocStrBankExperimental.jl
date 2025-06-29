```
AbstractMicrobe{D} <: AbstractAgent where {D<:Integer}
```

All microbe types in MicrobeAgents.jl simulations must be instances of user-defined types that are subtypes of `AbstractMicrobe`.     YourMicrobeType{D} <: AbstractMicrobe{D} The parameter `D` defines the dimensionality of the space in which the microbe type lives (1, 2 and 3 are supported).

All microbe types *must* have at least the following fields:

  * `id::Int` id of the microbe (used internally by Agents.jl)
  * `pos::SVectpr{D,Float64}` position of the microbe
  * `vel::SVector{D,Float64}` velocity of the microbe
  * `motility::AbstractMotility` motile pattern of the microbe
  * `turn_rate::Real` average reorientation rate of the microbe
  * `rotational_diffusivity::Real` coefficient of brownian rotational diffusion
  * `radius::Real` equivalent spherical radius of the microbe
  * `state::Real` generic variable for a scalar internal state
