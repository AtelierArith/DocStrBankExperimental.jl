```
struct KalmanSmoothingSolution
```

カルマン平滑化問題の解を表す構造体です。

# フィールド

  * `sol`: *フィルタリング* プロセスの結果を含む解オブジェクト。
  * `xT`: 平滑化された状態推定。
  * `RT`: 平滑化された状態共分散。

解オブジェクトはプロットできます。

```
plot(sol; plotxT=true, plotRT=true, kwargs...)
```

ここで

  * `plotxT`: 平滑化された推定値 `x(t|T)` をプロットします。
  * `plotRT`: 平滑化された共分散 `R(t|T)` を ±2σ (正確には 1.96 σ) のリボンとしてプロットします。
  * 残りのキーワード引数は [`KalmanFilteringSolution`](@ref) と同じです。

平滑化解をプロットする際には、フィルタリング解もプロットされます。プロットされる信号を制御するために、[`KalmanFilteringSolution`](@ref) と同じキーワード引数を使用できます。
