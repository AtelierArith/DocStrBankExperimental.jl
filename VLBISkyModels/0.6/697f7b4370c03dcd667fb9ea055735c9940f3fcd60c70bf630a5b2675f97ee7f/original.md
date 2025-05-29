```julia
struct PolarizedModel{TI, TQ, TU, TV} <: ComradeBase.AbstractPolarizedModel
```

Wrapped model for a polarized model. This uses the stokes representation of the image.

# Fields

  * `I`: Stokes I model

  * `Q`: Stokes Q Model

  * `U`: Stokes U Model

  * `V`: Stokes V Model
