```
MeanDateVelocityMapping <: VelocityMapping
```

Mean date velocity mapping. It is the most simple mapping one can build and it consists in taking the 2D vector field of ice velocity associated to a given mean date and compare it to the instantaneous ice surface velocity obtained from the ice flow model. It is valid only for ice surface velocities estimated from short time windows since the velocity can vary within this time window.

# Fields

  * `spatialInterp::Symbol`: The spatial interpolation to use to map the ice surface   velocity grid to the glacier grid. For the moment only `:nearest` is supported.
