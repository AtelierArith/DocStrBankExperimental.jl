```
solve_energy_balance(Ags::Union{C3Q, C4Q}; gb = simplegbQ(),
                     opt = SimpleOptical(), PAR = 1000.0μmol/m^2/s,
                     NIR = 250.0W/m^2, ws = 1.0m/s, RH = 0.75,
                     Tair = 298.0K, Ca = 400.0μmol/mol, P = 101.0kPa,
                     O2 = 210.0mmol/mol, order = Order2(), xatol = 0.01,
                     maxfnevals = 100, net = true)
solve_energy_balance(Ags::Union{C3, C4}; gb = simplegb(),
                     opt = SimpleOptical(), PAR = 1000.0, NIR = 250.0,
                     ws = 1.0, RH = 0.75, Tair = 298.0, Ca = 400.0,
                     P = 101.0e3, O2 = 210.0e3, order = Order2(), xatol = 0.01,
                     maxfnevals = 100, net = true)
```

Solve the leaf energy balance coupled to photosynthesis and transpiration.

# Arguments

  * `Ags`: Photosynthesis and stomatal conductance model
  * `gb`: Boundary layer conductance model
  * `opt`: Optical properties of the leaf
  * `PAR`: Photosynthetically active radiation (umol/m2/s)
  * `NIR`: Near-infrared radiation (W/m2)
  * `ws`: Wind speed (m/s)
  * `RH`: Relative humidity
  * `Tair`: Air temperature (K)
  * `Ca`: Atmospheric CO2 concentration (μmol/mol)
  * `P`: Air pressure (Pa)
  * `O2`: Atmospheric O2 concentration (μmol/mol)
  * `order`: Order of the root solving algorithm that finds leaf temperature         (see Roots.jl package for more information).
  * `xatol`: Absolute tolerance of the root solving algorithm (see Roots.jl package for more information),
  * `maxfnevals`: Maximum number of function evaluations of the root solving algorithm (see Roots.jl package for more information).
  * `net`: Whether to return net or gross CO2 assimilation.

# Details

Inputs maybe be either `Real` or `Quantity` types from Unitful.jl (i.e., with physical units). If `Quantity` types are used, the output will be a `Quantity` type.

# Returns

A named tuple with net CO2 assimilation (`An`, μmol/m^2/s), gross CO2 assimilation (`Ag`, μmol/m^2/s), transpiration (`Tr`, mol/m^2/s) and leaf temperature (`Tleaf`, K).
