```julia
struct IsAnalytic <: EHTModels.DensityAnalytic
```

Defines a trait that a states that a model is analytic. This is usually used with an abstract model where we use it to specify whether a model has a analytic fourier transform and/or image.
