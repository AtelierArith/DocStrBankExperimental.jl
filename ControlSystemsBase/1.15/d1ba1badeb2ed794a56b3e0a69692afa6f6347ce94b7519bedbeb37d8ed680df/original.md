```
sigmaplot(sys, args...; hz=false balance=true, extrema)
sigmaplot(LTISystem[sys1, sys2...], args...; hz=false, balance=true, extrema)
```

Plot the singular values of the frequency response of the `LTISystem`(s). A frequency vector `w` can be optionally provided.

  * If `hz=true`, the plot x-axis will be displayed in Hertz, the input frequency vector is still treated as rad/s.
  * `balance`: Call [`balance_statespace`](@ref) on the system before plotting.
  * `extrema`: Only plot the largest and smallest singular values.

`kwargs` is sent as argument to Plots.plot.
