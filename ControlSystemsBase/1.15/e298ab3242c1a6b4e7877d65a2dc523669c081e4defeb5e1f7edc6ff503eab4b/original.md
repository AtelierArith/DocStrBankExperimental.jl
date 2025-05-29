```
rgaplot(sys, args...; hz=false)
rgaplot(LTISystem[sys1, sys2...], args...; hz=false, balance=true)
```

Plot the relative-gain array entries of the `LTISystem`(s). A frequency vector `w` can be optionally provided.

  * If `hz=true`, the plot x-axis will be displayed in Hertz, the input frequency vector is still treated as rad/s.
  * `balance`: Call [`balance_statespace`](@ref) on the system before plotting.

`kwargs` is sent as argument to Plots.plot.
