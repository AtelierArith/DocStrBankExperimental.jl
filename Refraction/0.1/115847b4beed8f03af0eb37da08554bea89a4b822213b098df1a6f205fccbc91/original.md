```
transmittance(m::Material, wavelength::Real, distance::Real; [default::Real=0.0]) -> Real
```

Compute the transmittance of the material for a given wavelength and distance

# Arguments

  * `m::Material` : The material object
  * `wavelength::Real` : The wavelength at which the transmittance is to be computed given in $\mu m$.
  * `distance::Real` : The distance over which the transmittance is to be computed given in $\mu m$.
  * `default::Real=0.0` : The default value to return for the extinction coefficient if the material does not contain data on extinction coefficients
