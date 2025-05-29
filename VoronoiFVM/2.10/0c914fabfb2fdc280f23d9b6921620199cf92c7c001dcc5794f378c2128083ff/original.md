```
plothistory(tsol; 
            plots=[:timestepsizes,
                   :timestepupdates,
                   :newtonsteps,
                   :newtonupdates], 
            size=(700,600), 
            logmin=1.0e-20,
            Plotter=GridVisualize.default_plotter(),
            kwargs...)
```

Plot solution history stored in `tsol`. The `plots` argument allows to choose which plots are shown.
