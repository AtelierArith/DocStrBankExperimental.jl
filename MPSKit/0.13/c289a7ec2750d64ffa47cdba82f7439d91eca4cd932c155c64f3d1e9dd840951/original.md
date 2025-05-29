```julia
struct WII <: MPSKit.Algorithm
```

Generalization of the Euler approximation of the operator exponential for MPOs.

## Fields

  * `tol::Float64`: tolerance for convergence criterium
  * `maxiter::Int64`: maximal number of iterations

## References

  * [Zaletel et al. Phys. Rev. B 91 (2015)](@cite zaletel2015)
  * [Paeckel et al. Ann. of Phys. 411 (2019)](@cite paeckel2019)
