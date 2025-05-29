```
ρl = ref_rholsat(fluid::REFPROPSuperanc, T)
```

Returns the saturation liquid density for the reference fluid `fluid` at temperature `T`.

Inputs:

  * `fluid`: Reference fluid (an instance of `REFPROPSuperAnc`)
  * `T`: Temperature (Kelvin)

Outputs:

  * `ρl` : Saturation Liquid Density `[mol/m^3]`.  Returns `NaN` if the value is outside the range of the ancillary.
