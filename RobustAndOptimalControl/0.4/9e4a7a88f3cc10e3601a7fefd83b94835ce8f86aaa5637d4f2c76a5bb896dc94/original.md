```
muplot(sys, args...; hz=false)
muplot(LTISystem[sys1, sys2...], args...; hz=false)
```

Plot the structured singular values (assuming time-varying diagonal complex uncertainty) of the frequency response of the `LTISystem`(s). This plot is similar to `sigmaplot`, but scales the loop-transfer function to minimize the maximum singular value. Only applicable to square systems. A frequency vector `w` can be optionally provided.

If `hz=true`, the plot x-axis will be displayed in Hertz, the input frequency vector is still treated as rad/s.

`kwargs` is sent as argument to Plots.plot.
