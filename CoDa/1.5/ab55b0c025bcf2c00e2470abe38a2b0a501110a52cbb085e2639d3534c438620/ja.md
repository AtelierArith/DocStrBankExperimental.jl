```
variation(table)
```

`table`の変動行列`Τ`を返します。次の条件を満たします：

  * `Τ[i,j] = Var(log(x[i]/x[j]))` ただし `i, j = 1, ..., D`
