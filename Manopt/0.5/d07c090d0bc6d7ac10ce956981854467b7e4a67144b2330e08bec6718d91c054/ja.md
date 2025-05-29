```
get_residuals(M::AbstractManifold, nlso::NonlinearLeastSquaresObjective, p)
get_residuals!(M::AbstractManifold, V, nlso::NonlinearLeastSquaresObjective, p)
```

マニフォールド `M`、[`NonlinearLeastSquaresObjective`](@ref) `nlso`、および `M` 上の現在の点 $p$ に基づいて、残差ベクトル $f_i(p)$、$i=1,…,m$ を計算します。
