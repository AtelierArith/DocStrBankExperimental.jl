```julia
System(
    net_data::PowerSystems.PowerFlowDataNetwork;
    kwargs...
) -> PowerSystems.System

```

PowerModelsDataからSystemを構築します。

# 引数

  * `pfd_data::Union{PowerFlowDataNetwork, Union{String, IO}}`: PowerModelsデータオブジェクトまたはサポートされている

負荷フローケース (*.m, *.raw)

# キーワード引数

  * `ext::Dict`: ユーザー定義のパラメータを含みます。標準タイプのみを含むべきです。
  * `runchecks::Bool`: 入力フィールドおよびadd_component!が呼び出されたときに利用可能なチェックを実行します。エラーが見つかった場合はInvalidValueをスローします。
  * `time_series_in_memory::Bool=false`: HDF5の代わりにメモリに時系列データを保存します。
  * `config_path::String`: 検証設定ファイルへのパスを指定します。
  * `pm_data_corrections::Bool=true` : PowerModelsデータ修正を実行します（PowerModelsの:validateに相当）。
  * `import_all:Bool=false` : PTIファイルからすべてのフィールドをインポートします。

# 例

```julia
sys = System(
    pm_data, config_path = "ACTIVSg25k_validation.json",
    bus_name_formatter = x->string(x["name"]*"-"*string(x["index"])),
    load_name_formatter = x->strip(join(x["source_id"], "_"))
)
```
