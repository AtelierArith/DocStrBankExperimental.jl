```julia
struct BaseDiagnostics{P}
```

すべてのBaytesカーネルに含まれる診断出力の要約情報を格納します。

# フィールド

  * `ℓobjective::Float64`: ログ目的ターゲット結果。
  * `temperature::Float64`: ターゲット結果の温度
  * `prediction::Any`: 将来のデータの予測。
  * `iter::Int64`: カーネルの現在のイテレーション。
