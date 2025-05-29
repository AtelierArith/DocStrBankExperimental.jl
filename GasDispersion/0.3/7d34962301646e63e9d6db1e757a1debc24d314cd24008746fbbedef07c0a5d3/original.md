```
plume(::Scenario, BritterMcQuaidPlume[, equationset::EquationSet])
```

Returns the solution to the Britter-McQuaid continuous ground level release model for the given scenario.

The `equationset` is used to calculate the windspeed at 10m, all other  correlations are as per the Britter-McQuaid model. Unless otherwise specified a default power-law wind profile is used.

# References

  * Britter, Rex E. and J. McQuaid. 1988. *Workbook on the Dispersion of Dense Gases. HSE Contract Research Report No. 17/1988*
  * AIChE/CCPS. 1999. *Guidelines for Consequence Analysis of Chemical Releases*. New York: American Institute of Chemical Engineers
