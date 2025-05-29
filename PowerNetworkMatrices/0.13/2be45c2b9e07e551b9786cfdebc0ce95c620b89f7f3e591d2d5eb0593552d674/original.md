```julia
VirtualPTDF(
    sys;
    dist_slack,
    reduce_radial_branches,
    kwargs...
)

```

Builds the Virtual PTDF matrix from a system. The return is a VirtualPTDF struct with an empty cache.

# Arguments

  * `sys::PSY.System`:       PSY system for which the matrix is constructed

# Keyword Arguments

  * `dist_slack::Vector{Float64}=Float64[]`:       vector of weights to be used as distributed slack bus.       The distributed slack vector has to be the same length as the number of buse
  * `reduce_radial_branches::Bool=false`:       if True the matrix will be evaluated discarding       all the radial branches and leaf buses (optional, default value is false)
  * `kwargs...`:       other keyword arguments used by VirtualPTDF
