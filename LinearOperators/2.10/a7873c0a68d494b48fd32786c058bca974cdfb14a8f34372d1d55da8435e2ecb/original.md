```
DiagonalPSB(d)
```

Construct a linear operator that represents a diagonal PSB quasi-Newton approximation as described in

M. Zhu, J. L. Nazareth and H. Wolkowicz The Quasi-Cauchy Relation and Diagonal Updating. SIAM Journal on Optimization, vol. 9, number 4, pp. 1192-1204, 1999. https://doi.org/10.1137/S1052623498331793.

The approximation satisfies the weak secant equation and is not guaranteed to be positive definite.

# Arguments

  * `d::AbstractVector`: initial diagonal approximation.
