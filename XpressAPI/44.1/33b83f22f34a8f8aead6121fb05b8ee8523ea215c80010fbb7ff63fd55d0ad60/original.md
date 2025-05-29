```
XPRS_LPSTATUS
```

LP solution status. (integer)

Values: 0 : Unstarted (`XPRS_LP_UNSTARTED`). 1 : Optimal (`XPRS_LP_OPTIMAL`). 2 : Infeasible (`XPRS_LP_INFEAS`). 3 : Objective worse than cutoff (`XPRS_LP_CUTOFF`). 4 : Unfinished (`XPRS_LP_UNFINISHED`). 5 : Unbounded (`XPRS_LP_UNBOUNDED`). 6 : Cutoff in dual (`XPRS_LP_CUTOFF_IN_DUAL`). 7 : Problem could not be solved due to numerical issues. (`XPRS_LP_UNSOLVED`). 8 : Problem contains quadratic data, which is not convex (`XPRS_LP_NONCONVEX`). Consider using FICO Xpress Global.
