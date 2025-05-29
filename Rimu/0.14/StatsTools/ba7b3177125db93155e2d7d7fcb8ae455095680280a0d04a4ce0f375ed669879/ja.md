```
mixed_estimator_analysis(df::DataFrame; kwargs...)
mixed_estimator_analysis(sim::PMCSimulation; kwargs...)
-> (; df_me, correlation_estimate, se, se_l, se_u)

[`mixed_estimator`](@ref) を `DataFrame` `df` または [`PMCSimulation`](@ref Main.Rimu.PMCSimulation) `sim` に対して、[`solve`](@ref CommonSolve.solve(::ProjectorMonteCarloProblem)) から返されたものを、再重み付けの深さの範囲で繰り返し計算します。

`NamedTuple` を返し、フィールドは次の通りです。

  * `df_me`: 再重み付けの深さと `mixed_estiamator` データを含む `DataFrame`。以下の例を参照してください。
  * `correlation_estimate`: ブロッキング分析からの推定相関時間
  * `se, se_l, se_u`: [`shift_estimator`](@ref) と誤差

## キーワード引数

  * `h_range`: デフォルトは推定相関時間の2倍までの約 `h_values` 値
  * `h_values = 100`: 再重み付けの深さの最小数
  * `skip = 0`: 平均化から除外する初期時間ステップ
  * `threading = Threads.nthreads() > 1`: `false` の場合、進行状況メーターが表示されます
  * `shift_name = :shift` シフトデータを含む `df` の列の名前
  * `hproj_name = :hproj` 演算子オーバーラップデータを含む `df` の列の名前
  * `vproj_name = :vproj` プロジェクターオーバーラップデータを含む `df` の列の名前
  * `warn = true` ブロッキングが失敗したり、分母が小さい場合に警告メッセージをログに記録するかどうか

## 例

```

julia sim = solve(...) df*me, correlation*estimate, se, se*l, se*u = mixed*estimator*analysis(sim; skip=5_000)

using StatsPlots @df df*me plot(* -> se, :h, ribbon = (se*l, se*u), label = "⟨S⟩") # シフト推定器のための定数線とリボン @df df*me plot!(:h, :val, ribbon = (:val*l, :val*u), label="E*mix") # 再重み付けの深さの関数としての混合推定器 xlabel!("h")

```

参照: [`mixed_estimator`](@ref), [`growth_estimator_analysis`](@ref).
```
