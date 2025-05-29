```
C, kp, ki, fig, CF = loopshapingPI(P, ωp; ϕl, rl, phasemargin, form=:standard, doplot=false, Tf, F)
```

Selects the parameters of a PI-controller (on parallel form) such that the Nyquist curve of `P` at the frequency `ωp` is moved to `rl exp(i ϕl)`

The parameters can be returned as one of several common representations  chosen by `form`, the options are

  * `:standard` - $K_p(1 + 1/(T_i s) + T_d s)$
  * `:series` - $K_c(1 + 1/(τ_i s))(τ_d s + 1)$
  * `:parallel` - $K_p + K_i/s + K_d s$

If `phasemargin` is supplied (in degrees), `ϕl` is selected such that the curve is moved to an angle of `phasemargin - 180` degrees

If no `rl` is given, the magnitude of the curve at `ωp` is kept the same and only the phase is affected, the same goes for `ϕl` if no phasemargin is given.

  * `Tf`: An optional time constant for second-order measurement noise filter on the form `tf(1, [Tf^2, 2*Tf/sqrt(2), 1])` to make the controller strictly proper.
  * `F`: A pre-designed filter to use instead of the default second-order filter that is used if `Tf` is given.
  * `doplot` plot the `gangoffourplot` and `nyquistplot` of the system.

See also [`loopshapingPID`](@ref), [`pidplots`](@ref), [`stabregionPID`](@ref) and [`placePI`](@ref).
