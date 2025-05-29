```
LithosphericTemp(Tsurface=0.0, Tpot=1350.0, dTadi=0.5,
                    ubound="const", lbound="const, utbf = 50.0e-3, ltbf = 10.0e-3,
                    age = 120.0, dtfac = 0.9, nz = 201,
                    rheology = example_CLrheology()
                )
```

Calculates a 1D temperature profile [C] for variable thermal parameters including radiogenic heat source and     linearly interpolates the temperature profile onto the box. The thermal parameters are defined in     rheology and the structure of the lithosphere is define by LithosphericPhases().

# Parameters

  * Tsurface  : surface temperature [C]
  * Tpot      : potential mantle temperature [C]
  * dTadi     : adiabatic gradient [K/km]
  * ubound    : Upper thermal boundary condition ["const","flux"]
  * lbound    : Lower thermal boundary condition ["const","flux"]
  * utbf      : Upper thermal heat flux [W/m]; if ubound == "flux"
  * ltbf      : Lower thermal heat flux [W/m]; if lbound == "flux"
  * age       : age of the lithosphere [Ma]
  * dtfac     : Diffusion stability criterion to calculate T_age
  * nz        : Grid spacing for the 1D profile within the box
  * rheology  : Structure containing the thermal parameters for each phase [default example_CLrheology]
