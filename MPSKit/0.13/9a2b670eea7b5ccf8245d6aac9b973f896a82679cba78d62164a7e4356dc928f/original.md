```julia
struct DynamicalDMRG{F<:MPSKit.DDMRG_Flavour, S} <: MPSKit.Algorithm
```

A dynamical DMRG method for calculating dynamical properties and excited states, based on a variational principle for dynamical correlation functions.

## Fields

  * `flavour::MPSKit.DDMRG_Flavour`: flavour of the algorithm to use, either of type [`NaiveInvert`](@ref) or [`Jeckelmann`](@ref)
  * `solver::Any`: algorithm used for the linear solvers
  * `tol::Float64`: tolerance for convergence criterium
  * `maxiter::Int64`: maximal amount of iterations
  * `verbosity::Int64`: setting for how much information is displayed

## References

  * [Jeckelmann. Phys. Rev. B 66 (2002)](@cite jeckelmann2002)
