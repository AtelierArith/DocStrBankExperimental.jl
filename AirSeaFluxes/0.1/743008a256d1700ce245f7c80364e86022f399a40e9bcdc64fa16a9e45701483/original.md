```
AOGCM1D(ndays=60)
```

Atmosphere-Ocean, coupled, one-dimensional column model.

```
outputs,parameters=AOGCM1D(10)
p = dirname(pathof(AirSeaFluxes))
include(joinpath(p,"recipes_plots.jl"))
p1,p2,p3=plot_final(outputs,parameters)
display(p3)
```
