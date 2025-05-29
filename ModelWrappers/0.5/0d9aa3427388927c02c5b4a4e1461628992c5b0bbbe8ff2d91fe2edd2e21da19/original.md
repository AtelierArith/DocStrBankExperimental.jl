```julia
struct Objective{M<:ModelWrappers.ModelWrapper, D, T<:ModelWrappers.Tagged, F<:AbstractFloat} <: BaytesCore.AbstractObjective
```

Functor to calculate 'ℓfunc' and gradient at unconstrained 'θᵤ', including eventual Jacobian adjustments.

# Fields

  * `model::ModelWrappers.ModelWrapper`
  * `data::Any`
  * `tagged::ModelWrappers.Tagged`
  * `temperature::AbstractFloat`
