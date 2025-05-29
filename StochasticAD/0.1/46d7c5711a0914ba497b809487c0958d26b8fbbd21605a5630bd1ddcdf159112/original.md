```
StochasticTriple{T, V <: Real, FIs <: AbstractFIs{V}}
```

Stores the primal value of the computation, alongside a "dual" component representing an infinitesimal change, and a "triple" component that tracks discrete change(s) with infinitesimal probability. 

Pretty printed as "value + δε + ({pretty print of Δs})".

## Constructor

  * `value`: the primal value.
  * `δ`: the value of the almost-sure derivative, i.e. the rate of "infinitesimal" change.
  * `Δs`: alternate values with associated weights, i.e. Finite perturbations with Infinitesimal probability,       represented by a backend `FIs <: AbstractFIs`.
