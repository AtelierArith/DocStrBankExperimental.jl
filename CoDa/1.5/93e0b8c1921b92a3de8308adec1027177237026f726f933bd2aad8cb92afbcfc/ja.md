```
alrcov(table)
```

`table`の対数比共分散行列`Σ`を返します。これは次のようになります：

  * `Σ[i,j] = cov(log(x[i]/x[D]), log(x[j]/x[D]))` ただし `i, j = 1, ..., d`
