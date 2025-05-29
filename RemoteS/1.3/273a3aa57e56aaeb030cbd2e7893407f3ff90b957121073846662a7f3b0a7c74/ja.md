```
MCARI = mcari(green, red, redEdge1; kw...)
```

または

```
MCARI = mcari(cube::Union{String, GMTgrid}; [bands=Int[], bandnames=String[], layers=Int[]], kwargs...)
```

修正されたクロロフィル吸収比指数。Daughtery et al. 2000

MCARI = (redEdge1 - red - 0.2 * (redEdge1 - green)) * (redEdge1 / red)

（Sentinel-2 バンド 5 (VNIR)、バンド 4 (赤)、およびバンド 3 (緑)）。
