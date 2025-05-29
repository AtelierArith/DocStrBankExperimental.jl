```
axs = bode_plot(tf, log10_ω_min=-4.0, log10_ω_max=4.0, nb_pts=300)
```

draw the Bode plot of a transfer function `tf` to visualize its frequency response. returns the two axes of the plot for further tuning via `matplotlib` commands.

adjust the range of frequencies that the Bode plot presents with `log10_ω_min` and `log10_ω_max`.

increase the resolution of the Bode plot with `nb_pts`.

returns a `CairoMakie.jl` `Figure` object for further modification.
