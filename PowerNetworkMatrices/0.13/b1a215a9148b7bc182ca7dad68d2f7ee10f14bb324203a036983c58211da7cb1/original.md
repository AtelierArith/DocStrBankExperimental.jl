```julia
LODF(A, PTDFm; linear_solver, tol, reduce_radial_branches)

```

Builds the LODF matrix given the Incidence Matrix and the PTDF matrix of the system.

NOTE: tol is referred to the LODF sparsification, not the PTDF one. PTDF matrix must be considered as NON sparsified ("tol" argument not specified when calling the PTDF method).

# Arguments

  * `A::IncidenceMatrix`:       Structure containing the Incidence matrix of the system.
  * `PTDFm::PTDF`:       Strucutre containing the transposed PTDF matrix of the system.
  * `linear_solver::String`:       Linear solver to be used. Options are "Dense" and "KLU".
  * `tol::Float64`:       Tolerance to eliminate entries in the LODF matrix (default eps()).
  * `reduce_radial_branches::Bool`:       True to reduce the network by simplifying the radial branches and mapping the       eliminate buses
