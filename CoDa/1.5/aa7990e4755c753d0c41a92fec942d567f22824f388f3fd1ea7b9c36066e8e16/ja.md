```
lrarray(table)
```

`table`の変動配列 `A` を返します。次の条件を満たします：

  * `A[i,j] = E[log(x[i]/x[j])]` ただし `i > j`
  * `A[i,j] = Var(log(x[i]/x[j]))` ただし `i < j`
  * `A[i,j] = 0` ただし `i = j`
