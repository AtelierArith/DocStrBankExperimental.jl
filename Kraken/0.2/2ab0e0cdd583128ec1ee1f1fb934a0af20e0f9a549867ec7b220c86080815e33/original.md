```
find_kr(env, freq, p; n_points = 5_000, method = A42())

Find the horizontal wavenumbers for the Pekeris model.

# Arguments
- `env::PekerisUnderwaterEnv`: The underwater environment.
- `freq::Real`: The frequency of the signal.
- `p::Vector{Real}`: The Pekeris parameters.
- `n_points::Int=2_000`: The number of points to use in the search.
- `method::NonlinearSolver=NewtonRaphson()`: The method to use for the search.

# Returns
- `Vector{Real}`: The horizontal wavenumbers.
```
