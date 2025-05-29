```julia
VirtualLODF(sys; reduce_radial_branches, kwargs...)

```

Builds the Virtual LODF matrix from a system. The return is a VirtualLODF struct with an empty cache.

# Arguments

  * `sys::PSY.System`:       PSY system for which the matrix is constructed

# Keyword Arguments

  * `reduce_radial_branches::Bool=false`:       if True the matrix will be evaluated discarding       all the radial branches and leaf buses (optional, default value is false)
  * `kwargs...`:       other keyword arguments used by VirtualPTDF
