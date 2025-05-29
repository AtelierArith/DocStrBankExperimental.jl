```
moist_air(humidity [, pressure=c_p_ref, temp=c_T_ref])
```

Returns a component list for moist air at relative humidity with the corresponding abundances of all components. The pressure (in atm) and the temperature (in K) have to be provided otherwise the HITRAN defaults will be used.

!!! info "Valid range"
    Please note that the underlying model for the saturation vapor pressure uses separate models for water and ice. It should provide reasonable values within the range of 200 to 400 K and between 0.6 to 1.1 atm.

