```julia
VirtualPTDF(
    branches,
    buses;
    dist_slack,
    tol,
    max_cache_size,
    persistent_lines,
    radial_network_reduction
)

```

Builds the PTDF matrix from a group of branches and buses. The return is a VirtualPTDF struct with an empty cache.

# Arguments

  * `branches`:       Vector of the system's AC branches.
  * `buses::Vector{PSY.ACBus}`:       Vector of the system's buses.

# Keyword Arguments

  * `dist_slack::Vector{Float64} = Float64[]`:       Vector of weights to be used as distributed slack bus.       The distributed slack vector has to be the same length as the number of buses.
  * `tol::Float64 = eps()`:       Tolerance related to sparsification and values to drop.
  * `max_cache_size::Int`:       max cache size in MiB (inizialized as MAX*CACHE*SIZE_MiB).
  * `persistent_lines::Vector{String}`:       line to be evaluated as soon as the VirtualPTDF is created (initialized as empty vector of strings).
  * `radial_network_reduction::RadialNetworkReduction`:       Structure containing the radial branches and leaf buses that were removed       while evaluating the matrix
