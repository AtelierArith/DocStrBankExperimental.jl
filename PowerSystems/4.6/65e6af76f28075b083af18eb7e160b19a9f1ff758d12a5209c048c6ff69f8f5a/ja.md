```julia
System(
    pm_data::PowerSystems.PowerModelsData;
    kwargs...
) -> Any

```

PowerModelsDataからSystemを構築します。

# 引数

  * `pm_data::Union{PowerModelsData, Union{String, IO}}`: PowerModelsデータオブジェクトまたはサポートされている

負荷フローケース (*.m, *.raw)

# キーワード引数

  * `ext::Dict`: ユーザー定義のパラメータを含みます。標準タイプのみを含むべきです。
  * `runchecks::Bool`: 入力フィールドおよびadd_component!が呼び出されたときに利用可能なチェックを実行します。エラーが見つかった場合はInvalidValueをスローします。
  * `time_series_in_memory::Bool=false`: HDF5の代わりにメモリに時系列データを保存します。
  * `config_path::String`: 検証設定ファイルへのパスを指定します。
  * `pm_data_corrections::Bool=true` : PowerModelsデータの修正を実行します（別名: PowerModelsの:validate）。
  * `import_all:Bool=false` : PTIファイルからすべてのフィールドをインポートします。

# 例

```julia
sys = System(
    pm_data, config_path = "ACTIVSg25k_validation.json",
    bus_name_formatter = x->string(x["name"]*"-"*string(x["index"])),
    load_name_formatter = x->strip(join(x["source_id"], "_"))
)
```
