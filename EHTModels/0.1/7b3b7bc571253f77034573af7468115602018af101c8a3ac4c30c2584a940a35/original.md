```julia
struct NotAnalytic <: EHTModels.DensityAnalytic
```

Defines a trait that a states that a model is analytic. This is usually used with an abstract model where we use it to specify whether a model has does not have a easy analytic fourier transform and/or intensity function.
