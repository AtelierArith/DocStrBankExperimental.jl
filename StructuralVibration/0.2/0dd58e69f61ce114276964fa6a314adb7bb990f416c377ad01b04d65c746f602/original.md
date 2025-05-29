```
SdofForcedTimeProblem(sdof, u0, t, F, ω, type_exc)
```

Structure containing the data of a time problem for a sdof system subject to an arbitrary excitation

**Fields**

  * `sdof::Sdof`: Sdof structure
  * `F::AbstractVector`: Amplitude of the force excitation [N] or base motion [m]
  * `u0::AbstractVector`: Initial conditions

      * `x0`: Initial displacement [m]
      * `v0`: Initial velocity [m/s]
  * `t::AbstractRange`: Time points at which to evaluate the response
  * `type_exc::Symbol`: Type of excitation

      * `:force`: External force (default)
      * `:base`: Base motion
