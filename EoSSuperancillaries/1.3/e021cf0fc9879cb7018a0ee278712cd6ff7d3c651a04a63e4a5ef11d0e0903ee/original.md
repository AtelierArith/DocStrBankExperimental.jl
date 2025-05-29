```
vv = ref_vvsat(fluid::REFPROPSuperanc, T)
```

Returns the saturation vapour volume for the reference fluid `fluid` at temperature `T`.

Inputs:

  * `fluid`: Reference fluid (an instance of `REFPROPSuperAnc`)
  * `T`: Temperature (Kelvin)

Outputs:

  * `vv` : Saturation Vapour Volume `[m^3]`.  Returns `NaN` if the value is outside the range of the ancillary.
