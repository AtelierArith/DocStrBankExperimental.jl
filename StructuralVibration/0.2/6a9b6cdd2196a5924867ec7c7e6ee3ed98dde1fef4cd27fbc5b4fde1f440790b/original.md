```
SdofHarmonicTimeProblem(sdof, u0, t, F, ω, type_exc)
```

Structure containing the data of a time problem for a sdof system subject to a harmonic excitation

**Constructor parameters**

  * `sdof::Sdof`: Sdof structure
  * `F`: Amplitude of the force excitation [N] or base motion [m]
  * `f`: Frequency of the excitation [Hz]
  * `u0::AbstractVector`: Initial conditions

      * `x0`: Initial displacement [m]
      * `v0`: Initial velocity [m/s]
  * `t::AbstractRange`: Time points at which to evaluate the response
  * `type_exc::Symbol`: Type of excitation

      * `:force`: External force (default)
      * `:base`: Base motion

**Fields**

  * `sdof::Sdof`: Sdof structure
  * `F`: Amplitude of the force excitation [N] or base motion [m]
  * `ω`: Frequency of the excitation [rad/s]
  * `u0::AbstractVector`: Initial conditions

      * `x0`: Initial displacement [m]
      * `v0`: Initial velocity [m/s]
  * `t::AbstractRange`: Time points at which to evaluate the response
  * `type_exc::Symbol`: Type of excitation

      * `:force`: External force (default)
      * `:base`: Base motion
