```
passivityplot(sys, args...; hz=false)
passivityplot(LTISystem[sys1, sys2...], args...; hz=false)
```

Plot the passivity index of a `LTISystem`(s). The system is passive for frequencies where the index is < 0.

A frequency vector `w` can be optionally provided.

If `hz=true`, the plot x-axis will be displayed in Hertz, the input frequency vector is still treated as rad/s.

`kwargs` is sent as argument to Plots.plot.

See [`passivity_index`](@ref) for additional details. See also [`ispassive`](@ref), [`passivity_index`](@ref).
