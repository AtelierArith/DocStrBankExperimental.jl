```julia
get_rotframe_jacobian_response(
    res::HarmonicSteadyState.Result{D, S, P, F} where F<:FunctionWrappers.FunctionWrapper{Array{S, 2}, Tuple{Array{S, 1}}},
    Ω_range,
    branch::Int64;
    show_progress,
    damping_mod
)

```

Calculate the rotating frame Jacobian response for a given branch. Computes the rotating frame Jacobian response by evaluating eigenvalues of the numerical Jacobian and calculating the response magnitude for each frequency in the range.

# Arguments

  * `res::Result`: Result object containing the system's solutions
  * `Ω_range`: Range of frequencies to evaluate
  * `branch::Int`: Branch number to analyze
  * `show_progress=true`: Whether to show a progress bar
  * `damping_mod`: Damping modification parameter

# Returns

  * Array{P,2}: Response matrix in the rotating frame
