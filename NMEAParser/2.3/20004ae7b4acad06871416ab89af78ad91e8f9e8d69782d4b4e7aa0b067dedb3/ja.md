```
struct ZDA <: NMEAString
```

時刻と日付 (ZDA)

このNMEAデータ型は、GNSS受信機からの現在の時刻と日付に関する情報を表します。

# フィールド

  * `system::String`: GNSSシステム識別子（例：GPS、GLONASS、GALILEO、統合）。
  * `time::Float64`: 秒単位の時刻。
  * `day::Int`: 月の日。
  * `month::Int`: 年の月。
  * `year::Int`: 年。
  * `zone_hrs::Int`: 時間単位のタイムゾーンオフセット。
  * `zone_mins::Int`: 分単位のタイムゾーンオフセット。
  * `valid::Bool`: データの有効性を示すフラグ。

# コンストラクタ

```julia
ZDA(items::Array{D}; system::AbstractString = "UNKNOWN", valid = true) where D <: SubString
```

# 例

```julia
data = ZDA(["ZDA", "123456", "15", "02", "2024", "5", "30"])
```
