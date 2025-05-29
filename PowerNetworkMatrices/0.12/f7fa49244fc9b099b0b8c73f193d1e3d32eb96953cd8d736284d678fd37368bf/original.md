```julia
PTDF(
    A,
    BA;
    dist_slack,
    linear_solver,
    tol,
    reduce_radial_branches
)

```

Builds the PTDF matrix from a system. The return is a PTDF array indexed with the bus numbers.

# Arguments

  * `A::IncidenceMatrix`:       Incidence Matrix (full structure)
  * `BA::BA_Matrix`:       BA matrix (full structure)

# Keyword Arguments

  * `dist_slack::Vector{Float64}`:       Vector of weights to be used as distributed slack bus.       The distributed slack vector has to be the same length as the number of buses.
  * `linear_solver::String`:       Linear solver to be used. Options are "Dense", "KLU" and "MKLPardiso.
  * `tol::Float64`:       Tolerance to eliminate entries in the PTDF matrix (default eps()).
  * `reduce_radial_branches::Bool`:       True to reduce the network by simplifying the radial branches and mapping the       eliminate buses
