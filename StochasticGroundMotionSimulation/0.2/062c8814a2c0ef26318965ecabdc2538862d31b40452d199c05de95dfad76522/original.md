```
PathParameters
```

Custom type defining the path parameters of a Fourier spectrum. Consists of three other custom structs

  * `geometric` is a `GeometricSpreadingParameters` type
  * `saturation` is a `NearSourceSaturationParameters` type
  * `anelastic` is an `AnelasticAttenuationParameters` type

The base constructor is: `PathParameters(geo::G, sat::S, ane::A) where {G<:GeometricSpreadingParameters, S<:NearSourceSaturationParameters, A<:AnelasticAttenuationParameters}`

See also: [`FourierParameters`](@ref)
