```julia
LODF(
    branches,
    buses;
    linear_solver,
    tol,
    radial_network_reduction
)

```

Builds the LODF matrix given the data of branches and buses of the system.

# Arguments

  * `branches`:       vector of the System AC branches
  * `buses::Vector{PSY.ACBus}`:       vector of the System buses

# Keyword Arguments

  * `linear_solver`::String       linear solver to use for matrix evaluation.       Available options: "KLU", "Dense" (OpenBLAS) or "MKLPardiso".       Default solver: "KLU".
  * `tol::Float64`:       Tolerance to eliminate entries in the LODF matrix (default eps())
  * `radial_network_reduction::RadialNetworkReduction`:       Structure containing the radial branches and leaf buses that were removed       while evaluating the ma
