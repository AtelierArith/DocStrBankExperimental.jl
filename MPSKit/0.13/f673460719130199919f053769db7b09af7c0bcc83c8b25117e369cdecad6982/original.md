```
find_groundstate(ψ₀, H, [environments]; kwargs...) -> (ψ, environments, ϵ)
find_groundstate(ψ₀, H, algorithm, environments) -> (ψ, environments, ϵ)
```

Compute the groundstate for Hamiltonian `H` with initial guess `ψ`. If not specified, an optimization algorithm will be attempted based on the supplied keywords.

## Arguments

  * `ψ₀::AbstractMPS`: initial guess
  * `H::AbstractMPO`: operator for which to find the groundstate
  * `[environments]`: MPS environment manager
  * `algorithm`: optimization algorithm

## Keywords

  * `tol::Float64`: tolerance for convergence criterium
  * `maxiter::Int`: maximum amount of iterations
  * `verbosity::Int`: display progress information

## Returns

  * `ψ::AbstractMPS`: converged groundstate
  * `environments`: environments corresponding to the converged state
  * `ϵ::Float64`: final convergence error upon terminating the algorithm
