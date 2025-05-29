```
XPRS_BARPERTURB
```

Newton barrier: In numerically challenging cases it is often advantageous to apply perturbations on the KKT system to improve its numerical properties. (double)

`BARPERTURB` controlls how much perturbation is allowed during the barrier iterations. By default no perturbation is allowed. Set this parameter with care as larger perturbations may lead to less efficient iterates and the best settings are problem-dependent.

Default value: `0`

Domain: 0~+INF
