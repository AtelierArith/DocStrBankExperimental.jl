```
apply(x::TS, dim::Int=1; fun::Function=sum)
```

Apply function `fun` across dimension `dim` of a time series `x`.

  * If `dim` is 1, then apply `fun` to each row of `x`, returning a time series (`TS`) object of the results
  * If `dim` is 2, then apply `fun` to each column of `x`, returning an `Array` of the results
