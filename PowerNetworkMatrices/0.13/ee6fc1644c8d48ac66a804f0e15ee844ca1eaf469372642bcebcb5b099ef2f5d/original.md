```julia
PTDF(sys; dist_slack, reduce_radial_branches, kwargs...)

```

Builds the PTDF matrix from a system. The return is a PTDF array indexed with the bus numbers. Note that `dist_slack` and `reduce_radial_branches` kwargs are explicitly mentioned because needed inside of the function.

# Arguments

  * `sys::PSY.System`:       PSY system for which the matrix is constructed

# Keyword Arguments

  * `dist_slack::Vector{Float64}=Float64[]`:       vector of weights to be used as distributed slack bus.       The distributed slack vector has to be the same length as the number of buse
  * `reduce_radial_branches::Bool=false`:       if True the matrix will be evaluated discarding       all the radial branches and leaf buses (optional, default value is false)
