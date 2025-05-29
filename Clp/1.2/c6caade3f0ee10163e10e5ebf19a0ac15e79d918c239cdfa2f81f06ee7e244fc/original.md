```
Clp_loadProblem(model, numcols, numrows, start, index, value, collb, colub, obj, rowlb, rowub)
```

Loads a problem (the constraints on the rows are given by lower and upper bounds). If a pointer is NULL then the following values are the default: <ul> <li> <code>colub</code>: all columns have upper bound infinity <li> <code>collb</code>: all columns have lower bound 0 <li> <code>rowub</code>: all rows have upper bound infinity <li> <code>rowlb</code>: all rows have lower bound -infinity <li> <code>obj</code>: all variables have 0 objective coefficient </ul>

Just like the other loadProblem() method except that the matrix is given in a standard column major ordered format (without gaps).
