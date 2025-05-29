```
GainScheduledStateSpace(systems, vt; interpolator, x = zeros((systems[1]).nx), name, u0 = zeros((systems[1]).nu), y0 = zeros((systems[1]).ny))
```

A linear parameter-varying (LPV) version of [`Blocks.StateSpace`](@ref), implementing the following equations:

$$
\begin{aligned}
\dot{x} &= A(v) x + B(v) u \\
y        &= C(v) x + D(v) u
\end{aligned}
$$

where `v` is a scalar scheduling variable.

See example usage in the [gain-scheduling example](https://juliacontrol.github.io/ControlSystemsMTK.jl/dev/batch_linearization/#Gain-scheduling).

# Arguments:

  * `systems`: A vector of `ControlSystemsBase.StateSpace` objects
  * `vt`: A vector of breakpoint values for the scheduling variable `v`, this has the same length as `systems`.
  * `interpolator`: A constructor `i = interpolator(values, breakpoints)` and returns an interpolator object that can be called like `i(v)` to get the interpolated value at `v`. `LinearInterpolation` from DataInterpolations.jl is a good choice, but a lookup table can also be used.

# Connectors

  * `input` of type `RealInput` connects to $u$.
  * `output` of type `RealOutput` connects to $y$.
  * `scheduling_input` of type `RealInput` connects to $v$.
