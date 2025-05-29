```
C = pid(param_p, param_i, [param_d]; form=:standard, state_space=false, [Tf], [Ts], filter_order=2, d=1/√(2))
```

Calculates and returns a PID controller. 

The `form` can be chosen as one of the following (determines how the arguments `param_p, param_i, param_d` are interpreted)

  * `:standard` - $K_p(1 + 1/(T_i s) + T_d s)$
  * `:series` - $K_c(1 + 1/(τ_i s))(τ_d s + 1)$
  * `:parallel` - $K_p + K_i/s + K_d s$

If `state_space` is set to `true`, either `Kd` has to be zero or a positive `Tf` has to be provided for creating a filter on  the input to allow for a state-space realization.  A balanced state-space realization is returned, unless `balance = false`.

## Filter

If `Tf` is supplied, a filter is added, the filter used is either

  * `filter_order = 2` (default): $1 / ((sT_f)^2/(4d^2) + sT_f + 1)$ in series with the controller. Note: this parametrization of the filter differs in behavior from the common parameterizaiton $1/(s^2 + 2dws + w^2)$ as the parameters vary, the former maintains an almost fixed *bandwidth* while `d` varies, while the latter maintains a fixed distance of the poles from the origin.
  * `filter_order = 1`: $1 / (1 + sT_f)$ applied to the derivative term only

$T_f$ can typically be chosen as $T_i/N$ for a PI controller and $T_d/N$ for a PID controller, and `N` is commonly in the range 2 to 20. With a second-order filter, `d` controls the damping. `d = 1/√(2)` gives a Butterworth configuration of the poles, and `d=1` gives a critically damped filter (no overshoot). `d` above one may be used, although `d > 1` yields an increasingly over-damped filter (this parametrization does not send one pole to the origin $d → ∞$ like the $(ω,ζ)$ parametrization does).

## Discrete-time

For a discrete controller a positive `Ts` can be supplied. In this case, the continuous-time controller is discretized using the Tustin method.

## Examples

```
C1 = pid(3.3, 1, 2)                             # Kd≠0 works without filter in tf form
C2 = pid(3.3, 1, 2; Tf=0.3, state_space=true)   # In statespace a filter is needed
C3 = pid(2.,  3, 0; Ts=0.4, state_space=true)   # Discrete
```

The functions `pid_tf` and `pid_ss` are also exported. They take the same parameters and is what is actually called in `pid` based on the `state_space` parameter. See also [`pid_2dof`](@ref) for a 2DOF controller with inputs `[r; y]` and outputs `u`.
