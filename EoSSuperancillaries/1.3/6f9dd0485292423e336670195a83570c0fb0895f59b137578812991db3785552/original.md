```
ρv = ref_rhovsat(fluid::REFPROPSuperanc, T)
```

Returns the saturation vapour density for the reference fluid `fluid` at temperature `T`.

Inputs:

  * `fluid`: Reference fluid (an instance of `REFPROPSuperAnc`)
  * `T`: Temperature (Kelvin)

Outputs:

  * `ρv` : Saturation Vapour Density `[mol/m^3]`.  Returns `NaN` if the value is outside the range of the ancillary.
