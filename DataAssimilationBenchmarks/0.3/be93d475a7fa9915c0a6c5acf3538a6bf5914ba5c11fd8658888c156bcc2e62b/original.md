```
StepKwargs = Dict{String,Any}
```

Key word arguments for twin experiment time stepping. Arguments are given as:

REQUIRED:

  * `dx_dt`     - time derivative function with arguments x and dx_params
  * `dx_params` - parameters necessary to resolve dx_dt, not including parameters to be estimated in the extended state vector;
  * `h` - numerical time discretization step size

OPTIONAL:

  * `diffusion` - tunes the standard deviation of the Wiener process, equal to `sqrt(h) * diffusion`;
  * `diff_mat` - structure matrix for the diffusion coefficients, replaces the default uniform scaling;
  * `s_infl` - ensemble anomalies of state components are scaled by this parameter for calculation of emperical covariance;
  * `p_infl` - ensemble anomalies of extended-state components for parameter sample replicates are scaled by this parameter for calculation of emperical covariance, `state_dim` must be defined below;
  * `state_dim` - keyword for parameter estimation, specifying the dimension of the dynamic state, less than the dimension of full extended state;
  * `param_sample` - `ParamSample` dictionary for merging extended state with `dx_params`;
  * `ξ` - random array size `state_dim`, can be defined in `kwargs` to provide a particular realization for method validation;
  * `γ` - controls nonlinearity of the alternating*obs*operatori.

See [`DataAssimilationBenchmarks.ObsOperators.alternating_obs_operator`](@ref) for a discusssion of the `γ` parameter.
