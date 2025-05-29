```
PrescribedAtmosphere{FT, CA, DT} <: AbstractAtmosphericDrivers{FT}
```

Container for holding prescribed atmospheric drivers and other information needed for computing turbulent surface fluxes when driving land models in standalone mode.

The default CO2 concentration is a constant as a function of time, equal to 4.2e-4 mol/mol.

Since not all models require co2 concentration, the default for that is `nothing`.

  * `liquid_precip`: Precipitation (m/s) function of time: positive by definition
  * `snow_precip`: Snow precipitation (m/s) function of time: positive by definition
  * `T`: Prescribed atmospheric temperature (function of time)  at the reference height (K)
  * `u`: Prescribed wind speed (function of time)  at the reference height (m/s)
  * `q`: Prescribed specific humidity (function of time)  at the reference height (_)
  * `P`: Prescribed air pressure (function of time)  at the reference height (Pa)
  * `c_co2`: CO2 concentration in atmosphere (mol/mol)
  * `start_date`: Start date - the datetime corresponding to t=0 for the simulation
  * `h`: Reference height (m), relative to surface elevation
  * `gustiness`: Minimum wind speed (gustiness; m/s)
  * `thermo_params`: Thermodynamic parameters
