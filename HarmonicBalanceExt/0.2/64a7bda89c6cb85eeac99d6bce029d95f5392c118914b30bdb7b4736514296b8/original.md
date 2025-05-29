```julia
get_linear_response(
    res::HarmonicSteadyState.Result{D, S, P, F} where F<:FunctionWrappers.FunctionWrapper{Array{S, 2}, Tuple{Array{S, 1}}},
    nat_var::Symbolics.Num,
    Ω_range,
    branch::Int64;
    show_progress
) -> Matrix

```

Calculate the linear response of the system for a given branch. Evaluates the linear response by solving the linear response ODE for each stable solution and input frequency in the given range.

# Arguments

  * `res`: Result object containing the system's solutions
  * `nat_var::Num`: Natural variable to evaluate in the response
  * `Ω_range`: Range of frequencies to evaluate
  * `branch::Int`: Branch number to analyze
  * `show_progress=true`: Whether to show a progress bar

# Returns

  * Array{P,2}: Response matrix where rows correspond to frequencies and columns to stable solutions
