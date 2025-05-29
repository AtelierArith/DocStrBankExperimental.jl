```
coeff(a::AbsMSeries, n::Int)
```

Return the coefficient of the $n$-th nonzero term of the series (or zero if there are fewer than $n$ nonzero terms). Terms are numbered from the least significant term, i.e. the first term displayed when the series is printed.
