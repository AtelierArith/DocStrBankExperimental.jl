```julia
LODF(sys; reduce_radial_branches, kwargs...)

```

Builds the LODF matrix from a system. Note that `reduce_radial_branches` kwargs is explicitly mentioned because needed inside of the function.

# Arguments

  * `sys::PSY.System`:       Power Systems system

# Keyword Arguments

  * `reduce_radial_branches::Bool=false`:       if True the matrix will be evaluated discarding       all the radial branches and leaf buses (optional, default value is false)
