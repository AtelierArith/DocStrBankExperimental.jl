```
struct Material{MD<:MaterialData}
    name::String
    materialdata::MD
    wavelength_range::Tuple{Float64,Float64}
end
```

A material stores:

  * `name::String` : The name of the material, which is the path to the material in the database or a custom name when creating your own materials
  * `materialdata::{<:MaterialData}` : The material data, i.e the refractive index data and extinction coefficient data
  * `wavelength::Tuple{Float64, Float64}` : The wavelength range of the material data

!!! info
    Not every material in the database contains refractive indices and extinction coefficients. Some materials only contain refractive indices, while others only contain extinction coefficients.


The material object acts as a functor to compute the refractive index of the material for a given wavelength

```
(m::Material)(wavelength::Real; [, default::Real=0.0])
```

More information about the Functor method can be found here [`Material(wavelength::Real; default::Real)`](@ref)
