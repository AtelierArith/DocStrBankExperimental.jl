```
IndicatorLöhner (equivalent to IndicatorLoehner)

IndicatorLöhner(equations::AbstractEquations, basis;
                f_wave=0.2, variable)
IndicatorLöhner(semi::AbstractSemidiscretization;
                f_wave=0.2, variable)
```

AMR indicator adapted from a FEM indicator by Löhner (1987), also used in the FLASH code as standard AMR indicator. The indicator estimates a weighted second derivative of a specified variable locally.

When constructed to be used for AMR, pass the `semi`. Pass the `equations`, and `basis` if this indicator should be used for shock capturing.

## References

  * Löhner (1987) "An adaptive finite element scheme for transient problems in CFD" [doi: 10.1016/0045-7825(87)90098-3](https://doi.org/10.1016/0045-7825(87)90098-3)
  * [https://flash.rochester.edu/site/flashcode/user*support/flash4*ug_4p62/node59.html#SECTION05163100000000000000](https://flash.rochester.edu/site/flashcode/user_support/flash4_ug_4p62/node59.html#SECTION05163100000000000000)
