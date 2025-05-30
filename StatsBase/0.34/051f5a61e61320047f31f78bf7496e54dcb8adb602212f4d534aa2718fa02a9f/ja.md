```
ConvergenceException(iters::Int, lastchange::Real=NaN, tol::Real=NaN)
```

フィッティング手法は `iters` 回の反復で収束しませんでした。つまり、最終反復と前の反復のコストの間の `lastchange` が指定された許容誤差 `tol` よりも大きかったということです。
