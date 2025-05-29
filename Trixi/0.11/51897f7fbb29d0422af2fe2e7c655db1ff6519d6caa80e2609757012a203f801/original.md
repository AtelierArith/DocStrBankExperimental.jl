```
flux_godunov(u_ll, u_rr, orientation, equations::InviscidBurgersEquation1D)
```

Godunov (upwind) numerical flux for the inviscid Burgers' equation. See https://metaphor.ethz.ch/x/2019/hs/401-4671-00L/literature/mishra*hyperbolic*pdes.pdf , section 4.1.5 and especially equation (4.16).
