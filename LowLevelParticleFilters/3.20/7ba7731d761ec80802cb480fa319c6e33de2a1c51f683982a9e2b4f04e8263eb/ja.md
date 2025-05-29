```
sol = smooth(filtersol)
sol = smooth(kf::AbstractKalmanFilter, u::Vector, y::Vector, p=parameters(kf))
```

すべての入力出力データ `u,y` または [`forward_trajectory`](@ref) から得られた既存のフィルタリングソリューション `filtersol` に基づいて、状態 `xT` と共分散 `RT` の平滑化された推定値を持つ [`KalmanSmoothingSolution`](@ref) を返します。

返された平滑化は `plot(sol)` を使用してプロットできます。詳細については [`KalmanSmoothingSolution`](@ref) と [`KalmanFilteringSolution`](@ref) を参照してください。
