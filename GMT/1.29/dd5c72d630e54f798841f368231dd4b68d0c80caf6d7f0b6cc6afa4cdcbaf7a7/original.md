```
velo(cmd0::String="", arg1=nothing; kwargs...)
```

Plot velocity vectors, crosses, and wedges.

See full GMT (not the `GMT.jl` one) docs at [`velo`](http://docs.generic-mapping-tools.org/latest/supplements/seis/velo.html)

```julia
    velo(mat2ds([0. -8 0 0 4 6 0.5; -8 5 3 3 0 0 0.5], ["4x6", "3x3"]), pen=(0.6,:red), fill_wedges=:green, outlines=true, Se="0.2/0.39/18", arrow="0.3c+p1p+e+gred", region=(-15,10,-10,10), show=1)
```
