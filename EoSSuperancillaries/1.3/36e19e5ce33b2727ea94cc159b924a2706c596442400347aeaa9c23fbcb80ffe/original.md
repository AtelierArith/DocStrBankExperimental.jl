```
vv = vdw_vvsat(T,a,b)
```

Returns the saturation vapour volume of the vdW cubic equation of state.

Inputs:

  * `T`: Temperature (Kelvin)
  * `a`: Atraction parameter `[m^6*Pa/mol]`
  * `b`: Covolume `[m^3/mol]`

Outputs:

  * `vv` : Saturation Vapour Volume `[m^3]`. Returns `NaN` if the value is outside the range of the ancillary.
