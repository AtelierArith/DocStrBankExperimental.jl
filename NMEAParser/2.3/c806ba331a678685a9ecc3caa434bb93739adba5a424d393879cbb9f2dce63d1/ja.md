```
struct GBS <: NMEAString
```

GNSS衛星故障検出 (GBS)

このNMEAデータ型は、衛星故障検出に関する情報を表し、誤差推定と確率を含みます。

# フィールド

  * `system::String`: GNSSシステム識別子（例：GPS、GLONASS、GALILEO、統合）。
  * `time::Float64`: 秒単位の時間。
  * `lat_error::Float64`: 緯度誤差推定。
  * `long_error::Float64`: 経度誤差推定。
  * `alt_error::Float64`: 高度誤差推定。
  * `failed_PRN::Int`: 故障した衛星のPRN。
  * `prob_of_missed::Float64`: 検出漏れの確率。
  * `excluded_meas_err::Float64`: 除外された測定誤差。
  * `standard_deviation::Float64`: 測定の標準偏差。
  * `valid::Bool`: データの有効性を示すフラグ。

# コンストラクタ

```julia
GBS(items::Array{D}; system::AbstractString = "UNKNOWN", valid = true) where D <: SubString
```

# 例

```julia
data = GBS(["GBS", "123456", "0.1", "0.2", "0.3", "5", "0.01", "0.05", "0.02"])
```
