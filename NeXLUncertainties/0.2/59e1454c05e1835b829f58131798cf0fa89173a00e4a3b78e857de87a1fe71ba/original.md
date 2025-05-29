```
checkcovariance!(cov::AbstractMatrix)
```

Checks whether the matrix meets the criteria for a covariance matrix. (Square, non-negative diagonal elements, symmetric cov[r,c]==cov[c,r], and the correlation coefficient between -1.0 and 1.0).  The tests are approximate to handle rounding errors but when a symmetric pair of values are not precisely equal they are set equal and when the correlation coefficient is slightly outside [-1,1], it is restricted to within these bounds. Thus the input matrix can be modified, in ways that are probably benign, by this "check" function.
