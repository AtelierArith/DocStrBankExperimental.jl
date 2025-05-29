```
MCARI = mcari(green, red, redEdge1; kw...)
```

or

```
MCARI = mcari(cube::Union{String, GMTgrid}; [bands=Int[], bandnames=String[], layers=Int[]], kwargs...)
```

Modified Chlorophyll Absorption ratio index. Daughtery et al. 2000

MCARI = (redEdge1 - red - 0.2 * (redEdge1 - green)) * (redEdge1 / red)

(Sentinel-2 Band 5 (VNIR), Band 4 (Red) and Band 3 (Green)).
