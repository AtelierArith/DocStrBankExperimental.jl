```
refractivephasescreen(sm, im, Vx_km_per_s=0.0, Vy_km_per_s=0.0)
```

An abstract type for generating a refractive phase screen model corresponding to an image and computing the scattered average image.

  * `sm <: AbstractScatteringModel`
  * `im <: IntensityMap`
  * `Vx_km_per_s` and `Vy_km_per_s` are optional for moving phase screen, which is not yet implemented.
