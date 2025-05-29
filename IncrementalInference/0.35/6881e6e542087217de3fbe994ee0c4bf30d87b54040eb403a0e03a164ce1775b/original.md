```julia
calcHelix_T(; ...)
calcHelix_T(t_start; ...)
calcHelix_T(t_start, t_stop; ...)
calcHelix_T(
    t_start,
    t_stop,
    pointsperturn;
    direction,
    T,
    radius,
    spine_t,
    xr_t,
    yr_t,
    h
)

```

Generate generalized helix parameterized by a curve along "t-axis" (i.e. z-axis, assuming z(t)=t).  

Notes

  * Returns vectors for (`t`, `x,y`, and `yaw` angle).
  * Offset to t_start at origin and facing direction along +y-axis.
  * Use callbacks `xr_t(t)` and `yr_t(t)` to skew the helix with any desired curve, examples include

      * `xr_t = (t) -> (1/3)t` to generate helix pattern along x-axis,
      * or make spiral along t using xr*t, yr*t to generate a rose pattern on xy,
      * use `spine_t(t)=xr_t(t) + im*yr_t(t)` as shortcut for more complicated patterns,
      * note `xr_t` and `yr_t` are scaled by a factor `radius`, unscale the input by division if desired.
  * Use the function twice for simulated and noisy trajectories (i.e. easier Gauss-Markov processes)
  * Gradient (i.e. angle) calculations are on the order of 1e-8.

Related

[`RoME.generateGraph_Helix2D!`](@ref)
