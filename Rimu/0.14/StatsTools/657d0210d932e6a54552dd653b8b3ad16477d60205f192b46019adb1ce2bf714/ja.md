```
rayleigh_replica_estimator_analysis(df::DataFrame; kwargs...)
rayleigh_replica_estimator_analysis(sim::PMCSimulation; kwargs...)
-> (; df_rre, df_se)
```

`DataFrame` `df` または [`PMCSimulation`](@ref Main.Rimu.PMCSimulation) `sim` に対して、再重み付けの深さの範囲で繰り返し [`rayleigh_replica_estimator`](@ref) を計算します。

`NamedTuple` を返し、フィールドは次の通りです。

  * `df_rre`: 再重み付けの深さと `rayleigh_replica_estimator` データを含む `DataFrame`。以下の例を参照してください。
  * `df_se`: 各レプリカごとに1行の [`shift_estimator`](@ref) 出力を含む `DataFrame`

## キーワード引数

  * `h_range`: デフォルトは、推定された相関時間の2倍までの約 `h_values` 値
  * `h_values = 100`: 最小の再重み付けの深さの数
  * `skip = 0`: 平均化から除外する初期時間ステップ
  * `threading = Threads.nthreads() > 1`: `false` の場合、進行状況メーターが表示されます
  * `shift_name = "shift"`: `df` の列に対応するシフトデータの名前 `<shift>_1`, ...
  * `op_name = "Op1"`: `df` の列に対応する演算子オーバーラップの名前 `c1_<op_ol>_c2`, ...
  * `vec_name = "dot"`: `df` の列に対応するベクトル-ベクトルオーバーラップの名前 `c1_<vec_ol>_c2`, ...
  * `Anorm = 1`: 演算子オーバーラップデータをスケールするためのスカラー前因子
  * `warn = true`: ブロッキングが失敗したり、分母が小さい場合に警告メッセージをログに記録するかどうか

## 例

```julia
sim = solve(...)
df_rre, df_se = rayleigh_replica_estimator_analysis(sim; skip=5_000)

using StatsPlots
@df df_rre plot(_ -> se, :h, ribbon = (se_l, se_u), label = "⟨S⟩") # シフト推定器のための定数線とリボン
@df df_rre plot!(:h, :val, ribbon = (:val_l, :val_u), label="E_mix") # 再重み付けの深さの関数としてのレイリー商推定器
xlabel!("h")
```

参照: [`rayleigh_replica_estimator`](@ref), [`mixed_estimator_analysis`](@ref), [`AllOverlaps`](@ref Main.AllOverlaps).
