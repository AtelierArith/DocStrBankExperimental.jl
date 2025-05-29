```
S, PS, CS, T = gangoffour(P, C; minimal=true)
gangoffour(P::AbstractVector, C::AbstractVector; minimal=true)
```

Given a transfer function describing the plant `P` and a transfer function describing the controller `C`, computes the four transfer functions in the Gang-of-Four.

  * `S = 1/(1+PC)` Sensitivity function
  * `PS = (1+PC)\P` Load disturbance to measurement signal
  * `CS = (1+PC)\C` Measurement noise to control signal
  * `T = PC/(1+PC)` Complementary sensitivity function

If `minimal=true`, [`minreal`](@ref) will be applied to all transfer functions.
