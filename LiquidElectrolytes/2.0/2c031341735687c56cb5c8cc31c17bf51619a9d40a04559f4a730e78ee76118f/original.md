```
act_flux!(ic,dϕ,ck,cl,γk,γl,electrolyte; evelo=0)
```

Scharfetter-Gummel upwind flux expression based on  activities, see Fuhrmann, CPC 2015. As shown in Chainais-Hilliaret, Cances, Fuhrmann, Gaudeul, 2019, this is consistent to thermodynamic equilibrium but shows inferior convergence behavior.
