```
fig = nyquistplot(sys;                Ms_circles=Float64[], Mt_circles=Float64[], unit_circle=false, hz=false, critical_point=-1, kwargs...)
nyquistplot(LTISystem[sys1, sys2...]; Ms_circles=Float64[], Mt_circles=Float64[], unit_circle=false, hz=false, critical_point=-1, kwargs...)
```

Create a Nyquist plot of the `LTISystem`(s). A frequency vector `w` can be optionally provided.

  * `unit_circle`: if the unit circle should be displayed. The Nyquist curve crosses the unit circle at the gain crossover frequency.
  * `Ms_circles`: draw circles corresponding to given levels of sensitivity (circles around -1 with  radii `1/Ms`). `Ms_circles` can be supplied as a number or a vector of numbers. A design staying outside such a circle has a phase margin of at least `2asin(1/(2Ms))` rad and a gain margin of at least `Ms/(Ms-1)`.
  * `Mt_circles`: draw circles corresponding to given levels of complementary sensitivity. `Mt_circles` can be supplied as a number or a vector of numbers.
  * `critical_point`: point on real axis to mark as critical for encirclements
  * If `hz=true`, the hover information will be displayed in Hertz, the input frequency vector is still treated as rad/s.
  * `balance`: Call [`balance_statespace`](@ref) on the system before plotting.

`kwargs` is sent as argument to plot.
