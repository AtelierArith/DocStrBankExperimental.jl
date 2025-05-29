```
struct DTM <: NMEAString
```

データム参照 (DTM)

このNMEAデータ型は、データム参照に関する情報を表します。

# フィールド

  * `system::String`: GNSSシステム識別子（例：GPS、GLONASS、GALILEO、複合）。
  * `local_datum_code::String`: ローカルデータムコード。
  * `local_datum_subcode::String`: ローカルデータムサブコード。
  * `lat_offset::Float64`: 緯度オフセット（メートル単位）。
  * `long_offset::Float64`: 経度オフセット（メートル単位）。
  * `alt_offset::Float64`: 高度オフセット（メートル単位）。
  * `ref_datum::String`: 参照データム。
  * `valid::Bool`: データの有効性を示すフラグ。

# コンストラクタ

```julia
DTM(items::Array{D}; system::AbstractString = "UNKNOWN", valid = true) where D <: SubString
```

# 例

```julia
data = DTM(["DTM", "W84", "W", "0.5", "W", "1.0", "M", "W84"])
```
