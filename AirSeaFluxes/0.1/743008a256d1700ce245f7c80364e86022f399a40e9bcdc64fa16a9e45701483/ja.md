```
AOGCM1D(ndays=60)
```

大気-海洋、結合された一次元コラムモデル。

```
outputs,parameters=AOGCM1D(10)
p = dirname(pathof(AirSeaFluxes))
include(joinpath(p,"recipes_plots.jl"))
p1,p2,p3=plot_final(outputs,parameters)
display(p3)
```
