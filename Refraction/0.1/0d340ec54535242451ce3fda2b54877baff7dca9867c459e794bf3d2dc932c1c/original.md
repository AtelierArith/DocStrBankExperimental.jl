```
extinction(m::Material, wavelength::Real; [default::Float64=0.0]) -> Real
```

Compute the extinction coefficient of the material for a given wavelength. If the wavelength is outside the wavelength range of the material the method will clamp the wavelength to the range. In the case that the material does not contain data on the extinction coefficient of the material the method will return the default value.

# Arguments

  * `m::Material` : The material object for which the extinction coefficient is to be computed.
  * `wavelength::Real` : The wavelength at which the extinction coefficient is to be computed given in $\mu m$.
  * `default::Float64=0.0` : The default value to return if the material does not contain data on extinction coefficients
