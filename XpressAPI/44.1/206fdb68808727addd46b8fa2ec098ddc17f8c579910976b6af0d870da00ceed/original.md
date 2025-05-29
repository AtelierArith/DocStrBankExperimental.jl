```
XPRS_INDLINBIGM
```

During presolve, indicator constraints will be linearized using a BigM coefficient whenever that BigM coefficient is small enough. (double)

This control defines the largest BigM for which such a linearized version will be added to the problem in addition to the original constraint. If the BigM is even smaller than INDPRELINBIGM, then the original indicator constraint will additionally be dropped from the problem.

Default value: `1.0E+05`

Domain: [0,+INF]
