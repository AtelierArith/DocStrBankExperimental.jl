```julia
PowerSystemTableData(
    directory::AbstractString,
    base_power::Float64,
    user_descriptor_file::AbstractString;
    descriptor_file,
    generator_mapping_file,
    timeseries_metadata_file
) -> PowerSystems.PowerSystemTableData

```

CSVファイルに保存されているすべてのデータを読み込みます。データの一般的な形式は次のとおりです。フォルダー: gen.csv branch.csv bus.csv .. load.csv

# 引数

  * `directory::AbstractString`: CSVファイルを含むディレクトリ
  * `base_power::Float64`: システムの基準電力
  * `user_descriptor_file::AbstractString`: カスタマイズされた入力記述子ファイル
  * `descriptor_file=POWER_SYSTEM_DESCRIPTOR_FILE`: PowerSystems記述子ファイル
  * `generator_mapping_file=GENERATOR_MAPPING_FILE`: 発電機マッピング構成ファイル
