```julia
struct ConcordanceCrescent{T} <: VLBISkyModels.GeometricModel{T}
```

Creates the ConcordanceCrescent model, i.e. a flat-top crescent with a displacment and a slash and shadow depth. Note this creates a crescent with unit flux. If you want a different flux please use the `renomed` modifier.

## Fields

  * `router`: Outer radius of the crescent

  * `rinner`: Inner radius of the crescent (i.e. inside this radius there is a hole)

  * `shift`: Displacment of the inner disk radius

  * `slash`: Strength of the linear slash. Note that s∈[0.0,1.0] to ensure positivity in the image.

## Notes

Unlike the Gaussian and Disk models this does not create the unit version. In fact, this model could have been created using the `Disk` and primitives by using VLBISkyModels's model composition functionality.
