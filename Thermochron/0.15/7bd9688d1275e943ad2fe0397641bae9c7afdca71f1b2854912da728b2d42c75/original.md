```julia
rmr0model(F, Cl, OH, Mn=0, Fe=0, others=0)
```

Calculate rmr0 as a function of composition (specified in terms of atoms per fomula unit, or APFU) for "multikinetic" apatite fission  track thermochronology.

Implements equation 11 from Ketcham et al. 2007  (doi: 10.2138/am.2007.2281)

```
rmr0 = (-0.0495 -0.0348F +0.3528|Cl - 1| +0.0701|OH - 1| 
        -0.8592Mn -1.2252Fe -0.1721Others)^0.1433
```
