```
add_interaction!(ax)
add_interaction!(ax, p::_ABMPlot)
```

Adds model control buttons and parameter sliders according to the plotting keywords `add_controls` (if true) and `params` (if not empty). Buttons and sliders are placed next to each other in a new layout position below the position of `ax`.
