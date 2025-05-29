```
sys = ss(A, B, C, D)      # Continuous
sys = ss(A, B, C, D, Ts)  # Discrete
sys = ss(P::TransferFunction; balance=true, minimal=false) # Convert TransferFunction to StateSpace
```

Create a state-space model `sys::StateSpace{TE, T}` with matrix element type `T` and TE is `Continuous` or `<:Discrete`.

This is a continuous-time model if `Ts` is omitted. Otherwise, this is a discrete-time model with sampling period `Ts`.

`D` may be specified as `0` in which case a zero matrix of appropriate size is constructed automatically.  `sys = ss(D [, Ts])` specifies a static gain matrix `D`.

When a transfer function `P` is converted to a state-space model, the user may choose whether to balance the state-space model (default=true) and/or to return a minimal realization (default=false). This conversion has more keyword argument options, see `?ControlSystemsBase.MatrixPencils.rm2ls` for additional details.

To associate names with state variables, inputs and outputs, see [`named_ss`](https://juliacontrol.github.io/RobustAndOptimalControl.jl/dev/#Named-systems).
