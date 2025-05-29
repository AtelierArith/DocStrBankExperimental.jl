```
fig = bodeplot(sys, args...)
bodeplot(LTISystem[sys1, sys2...], args...; plotphase=true, balance = true, kwargs...)
```

Create a Bode plot of the `LTISystem`(s). A frequency vector `w` can be optionally provided. To change the Magnitude scale see [`setPlotScale`](@ref). The default magnitude scale is "log10" (absolute scale).

  * If `hz=true`, the plot x-axis will be displayed in Hertz, the input frequency vector is still treated as rad/s.
  * `balance`: Call [`balance_statespace`](@ref) on the system before plotting.
  * `adjust_phase_start`: If true, the phase will be adjusted so that it starts at -90*intexcess degrees, where `intexcess` is the integrator excess of the system.
  * `adaptive`: If true, an adaptive frequency grid is used in order to keep the number of plotted points low, while resolving features in the frequency response well. If a manually provided frequency vector is used, this may be downsampled before plotting.

`kwargs` is sent as argument to RecipesBase.plot.
