```
lrarray(table)
```

Return the variation array `A` of the `table` such that:

  * `A[i,j] = E[log(x[i]/x[j])]` for `i > j`
  * `A[i,j] = Var(log(x[i]/x[j]))` for `i < j`
  * `A[i,j] = 0` for `i = j`
