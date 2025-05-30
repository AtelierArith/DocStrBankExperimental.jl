```
ConvergenceException(iters::Int, lastchange::Real=NaN, tol::Real=NaN)
```

フィッティング手順は `iters` 回の反復で収束しませんでした。すなわち、最終反復と前回反復のコストの間の `lastchange` が指定された許容誤差 `tol` より大きかったためです。
