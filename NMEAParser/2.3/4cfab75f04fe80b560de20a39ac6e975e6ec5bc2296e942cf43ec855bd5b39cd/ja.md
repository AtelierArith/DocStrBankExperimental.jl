```
struct GGA <: NMEAString
```

GPSフィックスデータ (GGA)

このNMEAデータ型は、緯度、経度、高度、衛星の数、および精度測定を含むGPSフィックスに関する情報を表します。

# フィールド

  * `system::String`: GPS、GLONASS、GALILEO、または複合。
  * `time::Float64`: 秒単位の時間。
  * `latitude::Float64`: 小数度の緯度。
  * `longitude::Float64`: 小数度の経度。
  * `fix_quality::String`: フィックスの品質。
  * `num_sats::Int`: フィックスに使用された衛星の数。
  * `HDOP::Float64`: 水平精度の低下。
  * `altitude::Float64`: 平均海面上の高度（MSL）メートル単位。
  * `geoidal_separation::Float64`: ジオイドの分離メートル単位。
  * `age_of_differential::Float64`: 差分データの年齢。
  * `diff_reference_id::Int`: 差分基準局ID。
  * `valid::Bool`: データの有効性を示すフラグ。

# コンストラクタ

```julia
GGA(items::Array{D}; system::AbstractString = "UNKNOWN", valid = true) where D <: SubString
```

# 例

```julia
data = GGA(["GGA", "123456", "123.456", "N", "987.654", "W", "1", "8", "0.9", "123.4", "M", "54.3", "M", "1"])
```
