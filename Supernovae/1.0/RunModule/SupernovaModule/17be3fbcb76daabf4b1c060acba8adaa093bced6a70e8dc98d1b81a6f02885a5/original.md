```
mutable struct Supernova
```

A Supernova

# Fields

  * `name::String`: Supernova name
  * `zeropoint::typeof(1.0u"AB_mag")`: Zeropoint of the supernova
  * `redshift::Float64`: Redshift of the supernova
  * `lightcurve::[`Lightcurve`](@ref)`: The lightcurve of the supernova
