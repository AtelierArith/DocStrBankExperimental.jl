```
flux_ec(u_ll, u_rr, orientation, equations::InviscidBurgersEquation1D)
```

Entropy-conserving, symmetric flux for the inviscid Burgers' equation.

$$
F(u_L, u_R) = \frac{u_L^2 + u_L u_R + u_R^2}{6}
$$
