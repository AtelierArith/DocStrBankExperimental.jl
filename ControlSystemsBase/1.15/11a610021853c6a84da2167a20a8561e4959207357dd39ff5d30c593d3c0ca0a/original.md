```
result = lsim(sys, u[, t]; x0, method])
result = lsim(sys, u::Function, t; x0, method)
```

Calculate the time response of system `sys` to input `u`. If `x0` is omitted, a zero vector is used.

The result structure contains the fields `y, t, x, u` and can be destructured automatically by iteration, e.g.,

```julia
y, t, x, u = result
```

`result::SimResult` can also be plotted directly:

```julia
plot(result, plotu=true, plotx=false)
```

`y`, `x`, `u` have time in the second dimension. Initial state `x0` defaults to zero.

Continuous-time systems are simulated using an ODE solver if `u` is a function (requires using ControlSystems). If `u` is an array, the system is discretized (with `method=:zoh` by default) before simulation. For a lower-level interface, see `?Simulator` and `?solve`. For continuous-time systems, keyword arguments are forwarded to the ODE solver. By default, the option `dtmax = t[2]-t[1]` is used to prevent the solver from stepping over discontinuities in `u(x, t)`. This prevents the solver from taking too large steps, but may also slow down the simulation when `u` is smooth. To disable this behavior, set `dtmax = Inf`.

`u` can be a function or a *matrix* of precalculated control signals and must have dimensions `(nu, length(t))`. If `u` is a function, then `u(x,i)` (for discrete systems) or `u(x,t)` (for continuous ones) is called to calculate the control signal at every iteration (time instance used by solver). This can be used to provide a control law such as state feedback `u(x,t) = -L*x` calculated by `lqr`. To simulate a unit step at `t=t₀`, use `(x,t)-> t ≥ t₀`, for a ramp, use `(x,t)-> t`, for a step at `t=5`, use `(x,t)-> (t >= 5)` etc.

*Note:* The function `u` will be called once before simulating to verify that it returns an array of the correct dimensions. This can cause problems if `u` is stateful or has other side effects. You can disable this check by passing `check_u = false`.

For maximum performance, see function [`lsim!`](@ref), available for discrete-time systems only.

Usage example:

```julia
using ControlSystems
using LinearAlgebra: I
using Plots

A = [0 1; 0 0]
B = [0;1]
C = [1 0]
sys = ss(A,B,C,0)
Q = I
R = I
L = lqr(sys,Q,R)

u(x,t) = -L*x # Form control law
t  = 0:0.1:5
x0 = [1,0]
y, t, x, uout = lsim(sys,u,t,x0=x0)
plot(t,x', lab=["Position" "Velocity"], xlabel="Time [s]")

# Alternative way of plotting
res = lsim(sys,u,t,x0=x0)
plot(res)
```
