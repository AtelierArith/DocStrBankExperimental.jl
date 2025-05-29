```
Ap = prolong(A, [sz::Tuple])
```

Perform two-fold expansion in size. If `sz` is omitted, all dimensions are expanded. If `sz` is specified, it can be one of the following:

  * `sz[d] = size(A, d)`: no expansion is performed
  * `sz[d] = 2*size(A, d) - 1`: expansion to an odd-size, adding (by interpolation) points on the half-grid between all points along dimension `d`
  * `sz[d] = 2*size(A, d)`: expansion to an even-size, estimating the points on the 1/4 and 3/4 grid (including one point beyond either edge of the current span)

Any other choice results in an error. The default choice is to perform odd-expansion. `prolong` is normalized so as to approximately preserve the sum of `A`.

Thought of as an operator, `prolong` is equal to the transpose of `restrict`.
