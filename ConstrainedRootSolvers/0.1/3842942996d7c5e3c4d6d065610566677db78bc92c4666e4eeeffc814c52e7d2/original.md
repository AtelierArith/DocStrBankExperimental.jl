This method uses [`Bisection`](@ref) method to find the maximum. What this     method does is to

  * first calculate the `y`s at `x_min`, `x_mid`, and `x_max`
  * find the point where `y` is maximum
  * do bisection from the point to the `x_min` and `x_max`
  * update `x_min`, `x_mid`, and `x_max`

    find_peak(f::Function,             ms::BisectionMethod{FT},             tol::Union{ResidualTolerance{FT}, SolutionTolerance{FT}};             stepping::Bool = false   ) where {FT<:AbstractFloat}

Find the solution, given

  * `f` A function to solve
  * `ms` [`BisectionMethod`](@ref) type method struct
  * `tol` [`SolutionTolerance`](@ref) type tolerance struct
  * `stepping` Optional. If true, save the optimization steps to the history   field in method struct.
