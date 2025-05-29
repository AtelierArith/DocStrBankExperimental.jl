```
vl,vv = rk_vsat(T,a,b)
```

Returns the saturation liquid and vapour volumes of the Redlich-Kwong cubic equation of state.

Inputs:

  * `T`: Temperature (Kelvin)
  * `a`: Atraction parameter `[m^6*Pa/mol]`
  * `b`: Covolume `[m^3/mol]`

Outputs:

  * `vl` : Saturation Liquid Volume `[m^3]`.  Returns `NaN` if the value is outside the range of the ancillary.
  * `vv` : Saturation Vapour Volume `[m^3]`.  Returns `NaN` if the value is outside the range of the ancillary.
