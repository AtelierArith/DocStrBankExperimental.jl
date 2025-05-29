```
growth_estimator_analysis(df::DataFrame; kwargs...)
growth_estimator_analysis(sim::PMCSimulation; kwargs...)
-> (; df_ge, correlation_estimate, se, se_l, se_u)
```

`DataFrame` `df` または [`PMCSimulation`](@ref Main.Rimu.PMCSimulation) `sim` に対して、再重み付けの深さの範囲で繰り返し [`growth_estimator`](@ref) を計算します。

`NamedTuple` を返し、フィールドは次の通りです。

  * `df_ge`: 再重み付けの深さと `growth_estiamator` データを含む `DataFrame`。以下の例を参照してください。
  * `correlation_estimate`: ブロッキング分析からの推定相関時間
  * `se, se_l, se_u`: [`shift_estimator`](@ref) と誤差

## キーワード引数

  * `h_range`: デフォルトは推定相関時間の2倍までの約 `h_values` 値
  * `h_values = 100`: 最小の再重み付けの深さの数
  * `skip = 0`: 平均化から除外する初期時間ステップ
  * `threading = Threads.nthreads() > 1`: `false` の場合、進行状況メーターが表示されます
  * `shift_name = :shift` `df` 内のシフトデータの列名
  * `norm_name = :norm` `df` 内のウォーカーナンバーデータの列名
  * `warn = true` ブロッキングが失敗したり、分母が小さい場合に警告メッセージをログに記録するかどうか

## 例

```julia
sim = solve(...)
df_ge, correlation_estimate, se, se_l, se_u = growth_estimator_analysis(sim; skip=5_000)

using StatsPlots
@df df_ge plot(_ -> se, :h, ribbon = (se_l, se_u), label = "⟨S⟩") # シフト推定器のための定数線とリボン
@df df_ge plot!(:h, :val, ribbon = (:val_l, :val_u), label="E_gr") # 再重み付けの深さの関数としての成長推定器
xlabel!("h")
```

参照: [`growth_estimator`](@ref), [`mixed_estimator_analysis`](@ref).
