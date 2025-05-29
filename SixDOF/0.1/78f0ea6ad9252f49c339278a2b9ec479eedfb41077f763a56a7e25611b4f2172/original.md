```
StabilityDeriv(CL0, CLalpha, CLq, CLM, CLdf, CLde, alphas, 
    CD0, U0, exp_Re, e, Mcc, CDdf, CDde, CDda, CDdr, 
    CYbeta, CYp, CYr, CYda, CYdr, Clbeta, 
    Clp, Clr, Clda, Cldr, 
    Cm0, Cmalpha, Cmq, CmM, Cmdf, Cmde, 
    Cnbeta, Cnp, Cnr, Cnda, Cndr)
```

Stability derivatives of the aircraft.  Most are self explanatory if you are familiar with stability derivatives (e.g., CLalpha is dCL/dalpha or the lift curve slope). Some less familiar ones include

  * M: Mach number
  * alphas: the angle of attack for stall
  * U0: the speed for the reference Reynolds number CD0 was computed at
  * exp_Re: the coefficient in the denominator of the skin friction coefficient (0.5 laminar, 0.2 turbulent)
  * e: Oswald efficiency factor
  * Mcc: crest critical Mach number (when compressibility drag rise starts)
