```
Microbe{D,N} <: AbstractMicrobe{D,N}
```

Base microbe type for simple simulations. `D` is the space dimensionality and `N` is the number of states of the microbe's motility pattern.

`Microbe` has the required fields

  * `id::Int` an identifier used internally
  * `pos::SVector{D,Float64}` spatial position
  * `vel::SVector{D,Float64}` unit velocity vector
  * `speed::Float64` magnitude of the velocity vector
  * `motility::Motility{N}` motility pattern

and the default parameters

  * `rotational_diffusivity::Float64 = 0.0` coefficient of brownian rotational diffusion
  * `radius::Float64 = 0.0` equivalent spherical radius of the microbe
  * `state::Float64 = 0.0` generic variable for a scalar internal state
