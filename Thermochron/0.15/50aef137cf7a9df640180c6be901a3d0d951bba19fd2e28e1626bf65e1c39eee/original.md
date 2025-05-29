```julia
rmr0fromcl(Cl)
```

Calculate `rmr0` as a function of chlorine content `Cl` [APFU] for  "multikinetic" apatite fission track following the relation (Fig. 7a)  of Ketcham et al. 1999 (doi: 10.2138/am-1999-0903)

```
rmr0 = 1 - exp(2.107(1 - abs(Cl - 1)) - 1.834)
```
