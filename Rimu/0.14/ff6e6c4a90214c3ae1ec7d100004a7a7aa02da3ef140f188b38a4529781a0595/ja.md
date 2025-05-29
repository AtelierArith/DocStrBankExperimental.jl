```
solve!(sm::PMCSimulation; kwargs...)::PMCSimulation
```

[`Rimu.PMCSimulation`](@ref) を最後のステップが完了するまで、または壁時間制限に達するまで解決します。

以前に完了したシミュレーションを続行するには、キーワード引数を使用して新しい `last_step` または `wall_time` を設定します。オプションで、`replica_strategy`、`post_step_strategy`、または `reporting_strategy` に変更を加えることができます。

# オプションのキーワード引数:

  * `last_step = nothing`: 最後のステップを新しい値に設定し、シミュレーションを続行します。
  * `wall_time = nothing`: 許可される壁時間を新しい値に設定し、シミュレーションを続行します。
  * `reset_time = false`: `elapsed_time` カウンターをリセットし、シミュレーションを続行します。
  * `empty_report = false`: シミュレーションを続行する前にレポートを空にします。
  * `replica_strategy = nothing`: レプリカ戦略を変更します。レプリカの数がシミュレーション `sm` のレプリカの数と一致する必要があります。`empty_report = true` を含意します。
  * `post_step_strategy = nothing`: ポストステップ戦略を変更します。`empty_report = true` を含意します。
  * `reporting_strategy = nothing`: レポーティング戦略を変更します。`empty_report = true` を含意します。
  * `metadata = nothing`: レポートにメタデータを追加します。

[`ProjectorMonteCarloProblem`](@ref)、[`init`](@ref)、[`solve`](@ref)、[`step!`](@ref)、[`Rimu.PMCSimulation`](@ref) も参照してください。
