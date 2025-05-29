```
XPRS_AUTOPERTURB
```

Simplex: This indicates whether automatic perturbation is performed. (integer)

If this is set to `1`, the problem will be perturbed whenever the simplex method encounters an excessive number of degenerate pivot steps, thus preventing the Optimizer being hindered by degeneracies.

Default value: `1`

Values: 0 : No perturbation performed. 1 : Automatic perturbation is performed.
