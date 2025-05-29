```
currents(result,ispec; electrode)
```

Vector of electrode currents for species `ispec`. Electrode can be: 

  * `:bulk`: calculate current at bulk boundary conditions
  * `:we`: calculate current electrode interface
  * `:reaction`: calculate current from reaction term
