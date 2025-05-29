```
residuals(sp; kwargs...)
```

Calculate the residuals of the `ScalingProblem` around the optimal parameters or for a given parameter space.

# Arguments

  * `sp::ScalingProblem`: The `ScalingProblem` to calculate the residuals for.

# Keyword Arguments

  * `p_space::Vector{Vector{Float64}}`: The parameter space to calculate the residuals for.   If not provided, the parameter space is calculated from the optimal parameters,   their errors and the number of steps.
  * `N_steps::Int=50`: The number of steps to use for the default parameter space.
  * `dims::Vector{Int}=[1, ...]`: The dimensions to calculate the residuals for. If not   specified, all dimensions are used.

# Returns

  * `p_space::Vector{StepRangeLen}`: The parameter space used for the calculation.
  * `residuals::Array{Float64}`: The residuals for the given parameter space.

# Example

```julia
# lets say our xs, ys and Ls are data for the susceptibility of the Ising model
using ScalingCollapse
sp = ScalingProblem(xs, ys, Ls;
    sc=ScalingFunction(:xny; p_names=["T_c", "nu", "gamma"]),
    dx=[-1.0, 2.0],
)

# now we can calculate the residual landscape around the optimal parameters as follows:
p_space, residuals = residuals(sp)
# in the above case length(p_space) == 3 and size(residuals) == (50, 50, 50)

# we can specify the dimensions we are interested in as follows:
p_space, residuals = residuals(sp; dims=[1, 2])
# now length(p_space) == 2 and size(residuals) == (50, 50)
# we fixed the third parameter (in this case gamma) to its optimal value and calculated
# a 2D cut through the 3D residual landscape
```
