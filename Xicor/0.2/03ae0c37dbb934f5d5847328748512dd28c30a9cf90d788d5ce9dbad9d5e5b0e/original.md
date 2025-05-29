```
test_dependence(xi, X, Y; n_perm=1000, noties=false)
```

Computes a p-value and standard deviation quantifying the significance of the  correlation coefficient `xi` between `X` and `Y`. If `noties` is `true`, an  asymptotic test is used. If `noties` is `false`, a permutation test is used if  there are less than 20 observations, Otherwise, an asymptotic test is used based on the tie breaks of achieved by the `rank` function.
