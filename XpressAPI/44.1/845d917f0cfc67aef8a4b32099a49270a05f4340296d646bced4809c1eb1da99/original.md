```
XPRS_MIPSTATUS
```

(MIP) solution status. (integer)

Values: 0 : Problem has not been loaded (`XPRS_MIP_NOT_LOADED`). 1 : MIP search incomplete - the initial continuous relaxation has not been solved and no integer solution has been found (`XPRS_MIP_LP_NOT_OPTIMAL`). 2 : MIP search incomplete - the initial continuous relaxation has been solved and no integer solution has been found (`XPRS_MIP_LP_OPTIMAL`). 3 : MIP search incomplete - no integer solution found (`XPRS_MIP_NO_SOL_FOUND`). 4 : MIP search incomplete - an integer solution has been found (`XPRS_MIP_SOLUTION`). 5 : MIP search complete - no integer solution found (`XPRS_MIP_INFEAS`). 6 : MIP search complete - integer solution found (`XPRS_MIP_OPTIMAL`). 7 : MIP search incomplete - the initial continuous relaxation was found to be unbounded. A solution may have been found (`XPRS_MIP_UNBOUNDED`).
