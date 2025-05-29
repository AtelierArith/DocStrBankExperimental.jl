```
DiscretePID(; K = 1, Ti = false, Td = false, Tt = √(Ti*Td), N = 10, b = 1, umin = -Inf, umax = Inf, Ts, I = 0, D = 0, yold = 0)
```

A discrete-time PID controller with set-point weighting and integrator anti-windup. The controller is implemented on the standard form

$$
u = K \left( e + \dfrac{1}{Ti} \int e dt + T_d \dfrac{de}{dt} \right)
$$

$$
U(s) = K \left( bR(s) - Y(s) + \dfrac{1}{sT_i} \left( R(s) Y(s) \right) - \dfrac{sT_d}{1 + s T_d / N}Y(s)
$$

Call the controller like this

```julia
u = pid(r, y, uff) # uff is optional
u = calculate_control!(pid, r, y, uff) # Equivalent to the above
```

# Arguments:

  * `K`: Proportional gain
  * `Ti`: Integral time
  * `Td`: Derivative time
  * `Tt`: Reset time for anti-windup
  * `N`: Maximum derivative gain
  * `b`: Fraction of set point in proportional term
  * `umin`: Low output limit
  * `umax`: High output limit
  * `Ts`: Sampling period
  * `I`: Integral part
  * `D`: Derivative part
  * `yold`: Last measurement signal

See also [`calculate_control!`](@ref), [`set_K!`](@ref), [`set_Ti!`](@ref), [`set_Td!`](@ref), [`reset_state!`](@ref).
