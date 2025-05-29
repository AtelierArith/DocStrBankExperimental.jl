```julia
PTDF(
    branches,
    buses;
    dist_slack,
    linear_solver,
    tol,
    radial_network_reduction
)

```

Builds the PTDF matrix from a group of branches and buses. The return is a PTDF array indexed with the bus numbers.

# Arguments

  * `branches`:       vector of the System AC branches
  * `buses::Vector{PSY.ACBus}`:       vector of the System buses

# Keyword Arguments

  * `dist_slack::Vector{Float64}`:       vector of weights to be used as distributed slack bus.       The distributed slack vector has to be the same length as the number of buses
  * `linear_solver::String`:       Linear solver to be used. Options are "Dense", "KLU" and "MKLPardiso
  * `tol::Float64`:       Tolerance to eliminate entries in the PTDF matrix (default eps())
  * `radial_network_reduction::RadialNetworkReduction`:       Structure containing the radial branches and leaf buses that were removed       while evaluating the ma
