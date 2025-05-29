```
p = vdw_psat(T,a,b)
```

Returns the saturation pressure of the vdW cubic equation of state.

Inputs:

  * `T`: Temperature (Kelvin)
  * `a`: Atraction parameter `[m^6*Pa/mol]`
  * `b`: Covolume `[m^3/mol]`

Outputs:

  * `p` : Saturation pressure `[Pa]`.  Returns `NaN` if the value is outside the range of the ancillary.
