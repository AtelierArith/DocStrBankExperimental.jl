```
closedloop(l::LQGProblem, L = lqr(l), K = kalman(l))
```

Closed-loop system as defined in Glad and Ljung eq. 8.28. Note, this definition of closed loop is not the same as lft(P, K), which has B1 instead of B2 as input matrix. Use `lft(l)` to get the system from disturbances to controlled variables `w -> z`.

The return value will be the closed loop from filtred reference only, other disturbance signals (B1) are ignored. See [`feedback`](@ref) for a more advanced option. This function assumes that the control signal is computed as `u = r̃ - Lx̂` (not `u = L(xᵣ - x̂)`), i.e., the feedforward signal `r̃` is added directly to the plant input. `r̃` must thus be produced by an inverse-like model that takes state references and output the feedforward signal.

Use `static_gain_compensation` to adjust the gain from references acting on the input B2, `dcgain(closedloop(l))*static_gain_compensation(l) ≈ I`
