```
C, kp, ki, kd, fig, CF = loopshapingPID(P, ω; Mt = 1.3, ϕt=75, form=:standard, doplot=false, lb=-10, ub=10, Tf = 1/1000ω, F = nothing)
```

Selects the parameters of a PID-controller such that the Nyquist curve of the loop-transfer function $L = PC$ at the frequency `ω` is tangent to the circle where the magnitude of $T = PC / (1+PC)$ equals `Mt`. `ϕt` denotes the positive angle in degrees between the real axis and the tangent point.

The default values for `Mt` and `ϕt` are chosen to give a good design for processes with inertia, and may need tuning for simpler processes.

The gain of the resulting controller is generally increasing with increasing `ω` and `Mt`.

# Arguments:

  * `P`: A SISO plant.
  * `ω`: The specification frequency.
  * `Mt`: The magnitude of the complementary sensitivity function at the specification frequency, $|T(iω)|$.
  * `ϕt`: The positive angle in degrees between the real axis and the tangent point.
  * `doplot`: If true, gang of four and Nyquist plots will be returned in `fig`.
  * `lb`: log10 of lower bound for `kd`.
  * `ub`: log10 of upper bound for `kd`.
  * `Tf`: Time constant for second-order measurement noise filter on the form `tf(1, [Tf^2, 2*Tf/sqrt(2), 1])` to make the controller strictly proper. A practical controller typically sets this time constant slower than the default, e.g., `Tf = 1/100ω` or `Tf = 1/10ω`
  * `F`: A pre-designed filter to use instead of the default second-order filter.

The parameters can be returned as one of several common representations  chosen by `form`, the options are

  * `:standard` - $K_p(1 + 1/(T_i s) + T_ds)$
  * `:series` - $K_c(1 + 1/(τ_i s))(τ_d s + 1)$
  * `:parallel` - $K_p + K_i/s + K_d s$

See also [`loopshapingPI`](@ref), [`pidplots`](@ref), [`stabregionPID`](@ref) and [`placePI`](@ref).

# Example:

```julia
P  = tf(1, [1,0,0]) # A double integrator
Mt = 1.3  # Maximum magnitude of complementary sensitivity
ω  = 1    # Frequency at which the specification holds
C, kp, ki, kd, fig, CF = loopshapingPID(P, ω; Mt, ϕt = 75, doplot=true)
```
