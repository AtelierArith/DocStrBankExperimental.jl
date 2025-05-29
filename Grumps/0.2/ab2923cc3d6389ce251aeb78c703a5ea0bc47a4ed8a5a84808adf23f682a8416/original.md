```
VarξClustering( clusteron :: Symbol )
```

Creates a variable of type VarξClustering.  This is used to indicate that standard errors should be computed under the assumption of clustering.  This choice does not affect efficiency.  It also products an estimate of the matrix V(ξ) as part of the solution object, which can be used as an input into a possible second stage.  The argument is the variable one should cluster on, e.g. *VarξClustering( :market )* suggests that Grumps should cluster on the variable contained in the column in the products spreadsheet with column heading *market*.
