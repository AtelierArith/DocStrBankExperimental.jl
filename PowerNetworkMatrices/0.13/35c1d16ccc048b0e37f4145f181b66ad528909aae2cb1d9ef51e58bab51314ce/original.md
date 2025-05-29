```julia
LODF(A, ABA, BA; linear_solver, tol, reduce_radial_branches)

```

Builds the LODF matrix given the Incidence Matrix and the PTDF matrix of the system.

NOTE: this method does not support distributed slack bus.

# Arguments

  * `A::IncidenceMatrix`:       Structure containing the Incidence matrix of the system.
  * `ABA::ABA_Matrix`:       Structure containing the ABA matrix of the system.
  * `BA::BA_Matrix`:       Structure containing the transposed BA matrix of the system.
  * `linear_solver::String`:       Linear solver to be used. Options are "Dense" and "KLU".
  * `tol::Float64`:       Tolerance to eliminate entries in the LODF matrix (default eps()).
  * `reduce_radial_branches::Bool`:       True to reduce the network by simplifying the radial branches and mapping the       eliminate buses
