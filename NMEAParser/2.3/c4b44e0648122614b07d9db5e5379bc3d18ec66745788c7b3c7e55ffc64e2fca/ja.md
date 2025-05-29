```
struct GSV <: NMEAString
```

視界内の衛星 (GSV)

このNMEAデータ型は、視界内の衛星とその信号強度に関する情報を表します。

# フィールド

  * `system::String`: GNSSシステム識別子（例：GPS、GLONASS、GALILEO、複合）。
  * `msg_total::Int`: このサイクルのGSVメッセージの総数。
  * `msg_num::Int`: このGSVメッセージの番号。
  * `sat_total::Int`: 視界内の衛星の総数。
  * `SV_data::Vector{SVData}`: PRN、標高、方位、SNRを含む衛星データのベクター。
  * `valid::Bool`: データの有効性を示すフラグ。

# コンストラクタ

```julia
GSV(items::Array{D}; system::AbstractString = "UNKNOWN", valid = true) where D <: SubString
```

# 例

```julia
data = GSV(["GSV", "3", "1", "9", "1", "01", "30", "45", "20", "02", "60", "180", "25", "03", "15", "300", "15"])
```
