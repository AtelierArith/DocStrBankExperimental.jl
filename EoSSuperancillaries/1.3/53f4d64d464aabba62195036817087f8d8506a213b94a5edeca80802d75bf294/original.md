```
p = ref_psat(fluid::REFPROPSuperanc, T)
```

Returns the saturation pressure for the reference fluid `fluid` at temperature `T`.

Inputs:

  * `fluid`: Reference fluid (an instance of `REFPROPSuperAnc`)
  * `T`: Temperature (Kelvin)

Outputs:

  * `p` : Saturation Pressure `[Pa]`.  Returns `NaN` if the value is outside the range of the ancillary.
