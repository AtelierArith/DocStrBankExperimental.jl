```
solve_powerflow!(data::ACPowerFlowData; pf::ACPowerFlow{<:ACPowerFlowSolverType} = ACPowerFlow(), kwargs...)
```

与えられた電力フローデータに対して、マルチ期間AC電力フロー問題を解決します。

バスタイプは、無効電力制限が違反された場合にPVからPQに変更できます。

# 引数

  * `data::ACPowerFlowData`: グリッド情報と初期条件を含む電力フローデータ。
  * `pf::ACPowerFlow{<:ACPowerFlowSolverType}`: 電力フローソルバーのタイプ。デフォルトは`NewtonRaphsonACPowerFlow`です。
  * `kwargs...`: 追加のキーワード引数。

# キーワード引数

  * `check_connectivity::Bool`: グリッドが接続されているかどうかをチェックします。デフォルトは`true`です。
  * 'check*reactive*power_limits': `true`の場合、無効電力制限がPVからPQへのバスタイプの変更によって強制されます。デフォルトは`false`です。
  * `time_steps`: 解決する時間ステップを指定します。デフォルトは`data.timestep_map`のキーをソートして収集することです。

# 説明

この関数は、`data`で指定された各時間ステップのAC電力フロー問題を解決します。結果のためにメモリを事前に割り当て、ソートされた時間ステップを反復処理します。各時間ステップについて、`_ac_powerflow`関数を呼び出して電力フロー方程式を解決し、結果で`data`オブジェクトを更新します。電力フローが収束した場合、アクティブおよび無効電力注入、ならびに異なるバスタイプ（REF、PV、PQ）の電圧の大きさと角度を更新します。電力フローが収束しない場合、`data`の対応するエントリを`NaN`に設定します。最後に、支線の電力フローを計算し、`data`オブジェクトを更新します。

# 注意事項

  * グリッドトポロジーが変更された場合（例：変圧器のタップ位置や支線の運用状況）、アドミタンス行列`Yft`と`Ytf`を更新する必要があります。
  * `Yft`と`Ytf`が時間ステップ間で変更される場合、支線フロー計算はループ内に移動する必要があります。

# 例

```julia
solve_powerflow!(data)
```
