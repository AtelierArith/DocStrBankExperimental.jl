```
XPRS_BARREGULARIZE
```

This control determines how the barrier algorithm applies regularization on the KKT system. (integer)

Default value: `-1`

Values are a bitset: bit 0 : Standard regularization is turned on/off. bit 1 : Reduced regularization is turned on/off. This option reduces the perturbation effect of the standard regularization. bit 2 : Forces to keep dependent rows in the KKT system. bit 3 : Forces to preserve degenerate rows in the KKT system. bit 4 : Restrict regularization to infeasible iterates. bit 5 : Disable iterative regularizations. bit 6 : Apply iterative regularization more often.
