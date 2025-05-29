```
DIIS_extrapolation_alg
```

A struct representing the Direct Inversion in the Iterative Subspace (DIIS) extrapolation algorithm parameters.

# Fields

  * `M::Int`: Maximum number of iterations
  * `ΔM::Int`: Number of additional iterations after each DIIS step
  * `tol::Float64`: Convergence tolerance
  * `max_diis_step::Int`: Maximum number of DIIS steps
  * `damping_factor::Float64`: Factor used to stabilize the DIIS procedure
