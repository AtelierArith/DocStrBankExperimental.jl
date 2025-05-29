```
energybalance(pgb, pAgs, pEb, PAR, NIR, ws, RH, Tair, Ca, P, O2)
```

Calculate the energy balance of a leaf.

# Arguments

  * `pgb`: Boundary layer conductance model
  * `pAgs`: Photosynthesis and stomatal conductance model
  * `pEb`: Optical properties of the leaf
  * `PAR`: Photosynthetically active radiation (umol/m2/s)
  * `NIR`: Near-infrared radiation (W/m2)
  * `ws`: Wind speed (m/s)
  * `RH`: Relative humidity
  * `Tair`: Air temperature (K)
  * `Ca`: Atmospheric CO2 concentration (μmol/mol)
  * `P`: Air pressure (kPa)
  * `O2`: Atmospheric O2 concentration (μmol/mol)

# Details

Inputs maybe be either `Real` or `Quantity` types (i.e., with physical units). If `Quantity` types are used, the output will be a `Quantity` type.
