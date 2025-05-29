```
cair_sat(t::Real)
```

Humid air saturation specific in [kJ/kg-K] heat at 1 atmosphere, based on a correlation from EES.

# Arguments

  * `t`: T [K] good from 250K to 300K, no error bound checking is carried out.

# Ref

HumidAir::cair_sat(double);

# Note

Equals partial derivative of enthalpy with respect to temperature at constant relative humidity of 100 percent and pressure of 1 atmosphere.
