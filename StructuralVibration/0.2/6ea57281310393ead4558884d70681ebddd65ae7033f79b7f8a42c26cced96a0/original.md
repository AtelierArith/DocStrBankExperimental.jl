```
SdofFrequencyProblem(sdof, F, type_exc, type_resp)
```

Structure containing the data for computing the frequency response of a sdof system

**Fields**

  * `sdof::Sdof`: Sdof structure
  * `F::AbstractVector`: Vector of the force excitation [N] or base motion [m]
  * `freq::AbstractRange`: Vector of frequencies [Hz]
  * `type_exc::Symbol`: Type of excitation

      * `:force`: External force (default)
      * `:base`: Base motion
  * `type_resp::Symbol`: Type of response

      * `:dis`: Displacement spectrum(default)
      * `:vel`: Velocity spectrum
      * `:acc`: Acceleration spectrum
