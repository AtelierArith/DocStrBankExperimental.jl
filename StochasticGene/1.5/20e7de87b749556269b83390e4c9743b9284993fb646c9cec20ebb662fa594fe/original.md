```
prob_Gaussian_grid(par, reporters_per_state, Nstate, Ngrid, f::Function=kronecker_delta)
```

Generates a 3D array of Normal distributions based on the given parameters and reporters per state.

# Arguments

  * `par`: Parameters for the Gaussian distribution.
  * `reporters_per_state`: Number of reporters per state.
  * `Nstate`: Number of states.
  * `Ngrid`: Number of positions.
  * `f::Function`: Function to use for Kronecker delta (default is `kronecker_delta`).

# Returns

  * `Array{Distribution{Univariate,Continuous}}`: A 3D array of Normal distributions.
