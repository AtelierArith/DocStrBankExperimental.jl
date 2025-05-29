PowerSystems `System` から PowerModels データ辞書を作成します。結果のデータセットに時系列データを入力するには、`start_time` キーワード引数を渡し、単一の時間期間の場合は `period` を、複数の時間期間を持つマルチネットワークデータセットを作成する場合は `time_periods` を使用します。

# 引数

  * `sys::System`: PowerSystems システム

# キーワード引数

  * `name::String`: システム名
  * `start_time::DateTime`: `System` 予測初期時間
  * `time_periods::UnitRange{Int}=1:PSY.get_forecast_horizon(sys)`: 予測期間を選択するためのインデックス。妥当な範囲は `1:horizon`
  * `period::Int=1`: 予測期間を選択するためのインデックス。妥当なオプション
