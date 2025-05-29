A power system

`System`はPowerSystems.jlの主なデータコンテナで、基本的なメタデータ（基準電力、周波数）、コンポーネント（ネットワークトポロジー、負荷、発電機、サービス）、および時系列データを含みます。

```julia
System(base_power)
System(base_power, buses, components...)
System(base_power, buses, generators, loads, branches, storage, services; kwargs...)
System(base_power, buses, generators, loads; kwargs...)
System(file; kwargs...)
System(; buses, generators, loads, branches, storage, base_power, services, kwargs...)
System(; kwargs...)
```

# 引数

  * `base_power::Float64`: システムの基準電力値
  * `buses::Vector{ACBus}`: バスの配列
  * `components...`: 各要素（例：`buses`、`generators`、...）は、`Component`のサブタイプを含むイテラブルでなければなりません。

# キーワード引数

  * `ext::Dict`: ユーザー定義のパラメータを含みます。標準タイプのみを含むべきです。
  * `frequency::Float64`: (デフォルト = 60.0) 動作周波数（Hz）
  * `runchecks::Bool`: 入力フィールドおよびadd_component!が呼び出されたときに利用可能なチェックを実行します。エラーが見つかった場合はInvalidValueをスローします。
  * `time_series_in_memory::Bool=false`: HDF5の代わりにメモリに時系列データを保存します。
  * `time_series_directory::Union{Nothing, String}`: 時系列HDF5ファイルのディレクトリ。デフォルトはtmpファイルシステムです。
  * `enable_compression::Bool=false`: HDF5の時系列データの圧縮を有効にします。
  * `compression::CompressionSettings`: HDF5圧縮設定のカスタマイズを可能にします。
  * `config_path::String`: 検証設定ファイルへのパスを指定します。
  * `unit_system::String`: (デフォルト = `"SYSTEM_BASE"`) データの取得および設定時に[単位化](@ref per_unit)の単位システムを設定します（`"SYSTEM_BASE"`、`"DEVICE_BASE"`、または`"NATURAL_UNITS"`）。

デフォルトでは、時系列データはtmpファイルシステムのHDF5ファイルに保存され、大きなデータセットがシステムメモリを圧倒しないようにします（[データストレージ](@ref)を参照）。**システムの時系列データが利用可能なtmpスペースの量を超える場合**は、`time_series_directory`パラメータを使用してその場所を変更してください。また、環境変数`SIENNA_TIME_SERIES_DIRECTORY`を別のディレクトリに設定することで、場所を上書きすることもできます。

HDF5の圧縮はデフォルトでは有効になっていませんが、`enable_compression`を使用して有効にすることで、CPU時間のコストで大幅なストレージの節約を得ることができます。[`CompressionSettings`](@ref)を使用してHDF5圧縮をカスタマイズできます。

データセットがコンピュータのメモリに収まることがわかっている場合は、`time_series_in_memory`を使用してメモリに保存することでパフォーマンスを向上させることができます。

# 例

```julia
sys = System(100.0; enable_compression = true)
sys = System(100.0; compression = CompressionSettings(
    enabled = true,
    type = CompressionTypes.DEFLATE,  # BLOSCもサポートされています
    level = 3,
    shuffle = true)
)
sys = System(100.0; time_series_in_memory = true)
```
