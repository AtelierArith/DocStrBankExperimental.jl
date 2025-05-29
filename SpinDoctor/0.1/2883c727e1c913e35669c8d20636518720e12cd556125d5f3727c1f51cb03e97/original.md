```
Plotter(; nupdate = 1)
```

Plot the evolution of the BTPDE during time stepping. This requires loading the `GLMakie` plotting backend (`]add GLMakie; using GLMakie`). The plot is updated every `nupdate` time step. The resulting figure contains a plot of the time profile, total signal attenuation, and magnetization field (complex magnitude and phase shift).
