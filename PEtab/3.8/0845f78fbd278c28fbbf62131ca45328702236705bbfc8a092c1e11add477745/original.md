```
get_ps(res, prob::PEtabODEProblem; kwargs...)
```

Retrieve the `ODEProblem` parameter values for simulating the ODE model in `prob`. `res` can be a parameter estimation result (e.g., `PEtabMultistartResult`) or a `Vector` with parameters in the order expected by `prob` (see [`get_x`](@ref)).

See also: [`get_u0`](@ref), [`get_odeproblem`](@ref), [`get_odesol`](@ref).

## Keyword Arguments

  * `retmap=true`: Whether to return the values as a map in the form `[k1 => val1, ...]`. Such   a map can be directly used when building an `ODEProblem`. If `false`, a `Vector` is   returned. This keyword is only applicable for `get_u0` and `get_ps`.
  * `cid::Symbol`: Which simulation condition to return parameters for. If not provided,   defaults to the first simulation condition. For other `get` functions, the   `ODEProblem`, `u0`, or `ODESolution` for the specified `cid` is returned.
  * `preeq_id`: Which potential pre-equilibration (steady-state) simulation id to use.   If a valid `preeq_id` is provided, the ODE is first simulated to steady state for   `preeq_id`. Then the model shifts to `cid`, and the parameters for `cid` are returned.   For other `get` functions, the  `ODEProblem`, `u0`, or `ODESolution` for the   specified `cid` is returned
