Establishes the model for the network specified by type.

# Arguments

-`::Type{T}`: PowerModels AbstractPowerModel

# Accepted Key Words

  * `use_slacks::Bool`: Adds slacks to the network modeling
  * `PTDF::PTDF`: PTDF Array calculated using PowerNetworkMatrices
  * `duals::Vector{DataType}`: Constraint types to calculate the duals
  * `reduce_radial_branches::Bool`: Skips modeling radial branches in the system to reduce problem size

# Example

ptdf*array = PTDF(system) nw = NetworkModel(PTDFPowerModel, ptdf = ptdf*array),
