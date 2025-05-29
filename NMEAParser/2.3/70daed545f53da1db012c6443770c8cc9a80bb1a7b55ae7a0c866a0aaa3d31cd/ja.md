```
struct GSA <: NMEAString
```

GNSS DOP とアクティブ衛星 (GSA)

この NMEA データ型は、GNSS 精度の希薄度 (DOP) とナビゲーションに使用されるアクティブ衛星に関する情報を表します。

# フィールド

  * `system::String`: GNSS システム識別子 (例: GPS, GLONASS, GALILEO, Combined)。
  * `mode::Char`: 操作モード (A = 自動, M = 手動)。
  * `current_mode::Int`: 操作モード (1 = フィックスなし, 2 = 2D フィックス, 3 = 3D フィックス)。
  * `sat_ids::Vector{Int}`: フィックスに使用される衛星 ID のベクター。
  * `PDOP::Float64`: 位置精度の希薄度。
  * `HDOP::Float64`: 水平精度の希薄度。
  * `VDOP::Float64`: 垂直精度の希薄度。
  * `valid::Bool`: データの有効性を示すフラグ。

# コンストラクタ

```julia
GSA(items::Array{D}; system::AbstractString = "UNKNOWN", valid = true) where D <: SubString
```

# 例

```julia
data = GSA(["GSA", "M", "3", "1", "2", "3", "1.2", "0.9", "1.5"])
```
