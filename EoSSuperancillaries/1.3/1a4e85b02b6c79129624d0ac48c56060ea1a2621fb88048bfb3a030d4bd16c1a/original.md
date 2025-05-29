```
vl = ref_vlsat(fluid::REFPROPSuperanc, T)
```

Returns the saturation liquid volume for the reference fluid `fluid` at temperature `T`.

Inputs:

  * `fluid`: Reference fluid (an instance of `REFPROPSuperAnc`)
  * `T`: Temperature (Kelvin)

Outputs:

  * `vl` : Saturation Liquid Volume `[m^3]`.  Returns `NaN` if the value is outside the range of the ancillary.
