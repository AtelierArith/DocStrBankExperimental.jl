```
XPRS_PRICINGALG
```

Simplex: This determines the primal simplex pricing method. (integer)

It is used to select which variable enters the basis on each iteration. In general Devex pricing requires more time on each iteration, but may reduce the total number of iterations, whereas partial pricing saves time on each iteration, but may result in more iterations.

Default value: `0`

Values: -1 : Partial pricing. 0 : Determined automatically. 1 : Devex pricing. 2 : Steepest edge. 3 : Steepest edge with unit initial weights.
