```
sysd = c2d(sys::AbstractStateSpace{<:Continuous}, Ts, method=:zoh; w_prewarp=0)
Gd = c2d(G::TransferFunction{<:Continuous}, Ts, method=:zoh)
```

Convert the continuous-time system `sys` into a discrete-time system with sample time `Ts`, using the specified `method` (:`zoh`, `:foh`, `:fwdeuler` or `:tustin`).

`method = :tustin` performs a bilinear transform with prewarp frequency `w_prewarp`.

  * `w_prewarp`: Frequency (rad/s) for pre-warping when using the Tustin method, has no effect for other methods.

See also `c2d_x0map`

# Extended help

ZoH sampling is exact for linear systems with piece-wise constant inputs (step invariant), i.e., the solution obtained using [`lsim`](@ref) is not approximative (modulu machine precision). ZoH sampling is commonly used to discretize continuous-time plant models that are to be controlled using a discrete-time controller.

FoH sampling is exact for linear systems with piece-wise linear inputs (ramp invariant), this is a good choice for simulation of systems with smooth continuous inputs.

To approximate the behavior of a continuous-time system well in the frequency domain, the `:tustin` (trapezoidal / bilinear) method may be most appropriate. In this case, the pre-warping argument can be used to ensure that the frequency response of the discrete-time system matches the continuous-time system at a given frequency. The tustin transformation alters the meaning of the state components, while ZoH and FoH preserve the meaning of the state components. The Tustin method is commonly used to discretize a continuous-time controller.

The forward-Euler method generally requires the sample time to be very small relative to the time constants of the system, and its use is generally discouraged.

Classical rules-of-thumb for selecting the sample time for control design dictate that `Ts` should be chosen as $0.2 ≤ ωgc⋅Ts ≤ 0.6$ where $ωgc$ is the gain-crossover frequency (rad/s).
