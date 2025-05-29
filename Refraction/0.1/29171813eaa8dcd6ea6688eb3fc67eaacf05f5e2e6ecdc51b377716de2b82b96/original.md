```
dispersion(m::Material, wavelength::Real; [default::Real=1.0]) -> Real
```

Compute the refractive index of the material for a given wavelength. If the wavelength is outside the wavelength range of the material the method will clamp the wavelength to the range. In the case that the material does not contain data on the refractive indices of the material the method will return the default value.

# Arguments

  * `m::Material` : The material object for which the refractive index is to be computed.
  * `wavelength::Real` : The wavelength at which the refractive index is to be computed given in $\mu m$.
  * `default::Real=1.0` : The default value to return if the material does not contain data on refractive indices
