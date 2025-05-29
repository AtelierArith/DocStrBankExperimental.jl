```julia
rmr0fromdpar(dpar)
```

Calculate `rmr0` as a function of `dpar` for "multikinetic" apatite  fission track following the relation (Fig. 7b) of Ketcham et al. 1999 (doi: 10.2138/am-1999-0903)

```
rmr0 = 1 - exp(0.647(dpar-1.75) - 1.834)
```
