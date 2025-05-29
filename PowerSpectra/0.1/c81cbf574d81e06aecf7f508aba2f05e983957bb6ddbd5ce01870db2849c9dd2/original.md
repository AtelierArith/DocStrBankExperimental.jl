```
master(map₁::PolarizedHealpixMap, maskT₁::HealpixMap, maskP₁::HealpixMap,
       map₂::PolarizedHealpixMap, maskT₂::HealpixMap, maskP₂::HealpixMap; already_masked=false)
```

Perform a mode-decoupling calculation for two polarized maps, along with masks to apply. Returns spectra for $TT$, $TE$, $ET$, $EE$, $EB$, $BE$, and $BB$.

# Arguments:

  * `map₁::PolarizedHealpixMap`: the first IQU map
  * `maskT₁::HealpixMap`: mask for first map's intensity
  * `maskP₁::HealpixMap`: mask for first map's polarization
  * `map₂::PolarizedHealpixMap`: the second IQU map
  * `maskT₂::HealpixMap`: mask for second map's intensity
  * `maskP₂::HealpixMap`: mask for second map's polarization

# Keywords

  * `already_masked::Bool=false`: are the input maps already multiplied with the masks?
  * `lmin::Int=0`: minimum multipole

# Returns:

  * `Dict{Symbol,SpectralVector}`: spectra `Dict`, indexed with `:TT`, `:TE`, `:ET`, etc.
