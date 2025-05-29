```julia
struct BicubicPulse{T} <: VLBISkyModels.Pulse
```

```
BicubicPulse(b = 0.5)
```

The bicubic pulse for imaging. This pulse tends to have a flat spectrum but for most values of `b` can produce negative intensities in an image. This is the pulse used in [`Broderick et al. 2020`](https://iopscience.iop.org/article/10.3847/1538-4357/ab9c1f).
