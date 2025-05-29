`LAS`は、ポイントクラウドデータをASPRSの「LAS」形式で表現し、[`PointRecord`](@ref)のコレクションとポイントクラウドデータを説明するいくつかのグローバル属性で構成されています。データの要約を取得するには[`Base.show`](https://docs.julialang.org/en/v1/base/io-network/#Base.show-Tuple%7BIO,%20Any%7D)を使用し、インデックスを使用してポイントレコードにアクセスし、プロパティアクセス（例：`las.project_id`）を使用してグローバル属性を読み取り、[`update`](@ref update(::LAS, ::NamedTuple))を使用してグローバルおよびポイントごとの属性を変更します。

# ポイントデータレコード

`LAS`の[`PointRecord`](@ref)はインデックスを通じてアクセスできます。ファイルから`LAS`データを読み込む際（例：[`LAS(filename)`](@ref PointClouds.IO.LAS(::IO)))、ポイントレコードはデフォルトではメモリに読み込まれません。代わりに、データはアクセスされるときに遅延的に読み込まれ、メモリに収まらないファイルで作業することができます。`LAS`の`points`フィールドはポイントレコードの内部表現にアクセスしますが、直接の使用は推奨されません。

ポイントレコードは通常、`PointRecord{0}`から`PointRecord{10}`までの11の標準化されたポイントデータレコード形式（PDRF）に格納されます。すべてのPDRFは、3D座標やリターン強度などの多くの属性を共通して持っていますが、PDRFはサポートする属性の正確なセットとデータが保存される精度が異なります。LASバージョン1.4以降、PDRF 0–5はレガシーフォーマットと見なされ、新しいPDRF 6–10が推奨されます。

属性にアクセスするために呼び出すことができる関数のリストについては、[`PointRecord`](@ref)のヘルプテキストを参照してください。これらのアクセサ関数は、ポイント属性にアクセスするために1つまたは複数のインデックスを使用して`LAS`に直接呼び出すこともできます。

# 可変長レコード（VLR）

LASファイルの可変長レコードは、座標参照系（CRS）に関する情報を格納し、[`getcrs`](@ref)関数を使用してアクセスできます。生のVLRデータは、`LAS`の`vlr`フィールドを通じてアクセスできます。

# グローバルポイントクラウド属性

  * `coord_scale::NTuple{3,Float64}`
  * `coord_offset::NTuple{3,Float64}`
  * `coord_min::NTuple{3,Float64}`
  * `coord_max::NTuple{3,Float64}`
  * `return_counts::Vector{UInt64}`
  * `version::Tuple{UInt8,UInt8}`: LASファイル形式のバージョン（1.0から1.4）を`(major, minor)`タプルの形式で示します。
  * `source_id::UInt16`
  * `project_id::GUID`
  * `system_id::String`
  * `software_id::String`
  * `creation_date::Tuple{UInt16,UInt16}`
  * `has_adjusted_standard_gps_time::Bool`
  * `has_internal_waveform::Bool`
  * `has_external_waveform::Bool`
  * `has_synthetic_return_numbers::Bool`
  * `has_well_known_text::Bool`
