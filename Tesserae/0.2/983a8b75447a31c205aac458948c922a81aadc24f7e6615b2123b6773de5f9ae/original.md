```
uGIMP()
```

A kernel for the unchanged generalized interpolation material point (uGIMP) [^GIMP]. `uGIMP` requires the initial particle length `l` in the particle property as follows:

```jl
ParticleProp = @NamedTuple begin
    < variables... >
    l :: Float64
end
```

[^GIMP]: [Bardenhagen, S. G., & Kober, E. M. (2004). The generalized interpolation material point method. *Computer Modeling in Engineering and Sciences*, 5(6), 477-496.](https://doi.org/10.3970/cmes.2004.005.477)
