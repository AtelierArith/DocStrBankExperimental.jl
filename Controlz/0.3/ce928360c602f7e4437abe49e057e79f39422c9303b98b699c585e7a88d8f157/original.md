```
nyquist_diagram(tf, nb_pts=500, ω_max=10.0, savename=nothing)
```

plot the Nyquist diagram for a transfer function `tf` to visualize its frequency response. `s=-1` is plotted as a red `+`. `nb_pts` changes the resolution. `ω_max` gives maximum frequency considered.

returns a `CairoMakie.jl` `Figure` object for further modification.
