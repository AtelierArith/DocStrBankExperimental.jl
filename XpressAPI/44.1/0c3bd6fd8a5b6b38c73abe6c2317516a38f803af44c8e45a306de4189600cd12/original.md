```
XPRS_OPTIMIZETYPEUSED
```

The type of solver used in the last call to XPRSoptimize, XPRSmipoptimize, XPRSlpoptimize or `XPRSnlpoptimize`. (integer)

Values: -1 : No solver was selected yet (`XPRS_OPTIMIZETYPE_NONE`). This can occur if the solve was interrupted while determining the problem type. 0 : The LP solver was selected (`XPRS_OPTIMIZETYPE_LP`). The LP algorithm used by default is controlled by DEFAULTALG. 1 : The MIP solver was selected (`XPRS_OPTIMIZETYPE_MIP`). 2 : A local nonlinear solver was selected (`XPRS_OPTIMIZETYPE_LOCAL`). See XPRS*LOCALSOLVERSELECTED for which local solver was selected. 3 : The global nonlinear solver was selected (`XPRS*OPTIMIZETYPE_GLOBAL`).
