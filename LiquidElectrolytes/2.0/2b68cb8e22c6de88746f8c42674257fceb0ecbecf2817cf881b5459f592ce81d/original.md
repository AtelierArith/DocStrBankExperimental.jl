```
cent_flux!(ic,dϕ,ck,cl,γk,γl,electrolyte; evelo = 0)
```

Flux expression based on central differences, see Gaudeul/Fuhrmann 2022. As shown in the paper  this is covergent,  consistent to thermodynamic equilibrium but may show  inferior convergence behavior.
