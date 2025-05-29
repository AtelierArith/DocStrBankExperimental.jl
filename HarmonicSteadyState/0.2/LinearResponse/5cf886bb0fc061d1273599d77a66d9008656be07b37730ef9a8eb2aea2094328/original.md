```julia
get_jacobian_response(
    res::HarmonicSteadyState.Result{D, S, P, F} where F<:FunctionWrappers.FunctionWrapper{Array{S, 2}, Tuple{Array{S, 1}}},
    nat_var::Symbolics.Num,
    Ω_range,
    branch::Int64;
    show_progress
) -> Matrix

```

Calculate the Jacobian response spectrum for a given system. Computes the magnitude of the Jacobian response for stable solutions across specified frequency ranges.

# Arguments

  * `res::Result`: Result object containing the system's solutions
  * `nat_var::Num`: Natural variable to evaluate in the response
  * `Ω_range`: Range of frequencies to evaluate
  * `branch::Int` or `followed_branches::Vector{Int}`: Branch number(s) to analyze
  * `show_progress=true`: Whether to show a progress bar
  * `force=false`: Force recalculation of spectrum even if already exists

# Returns

  * Array{P,2}: Complex response matrix where rows correspond to frequencies and columns to solutions
