```
struct GLL <: NMEAString
```

地理緯度と経度 (GLL)

このNMEAデータ型は、地理的な緯度と経度に関する情報を表します。

# フィールド

  * `system::String`: GNSSシステム識別子（例：GPS、GLONASS、GALILEO、統合）。
  * `latitude::Float64`: 小数度での緯度。
  * `longitude::Float64`: 小数度での経度。
  * `time::Float64`: 秒単位の時間。
  * `status::Bool`: ステータスインジケーター（有効なフィックスの場合はtrue、そうでない場合はfalse）。
  * `mode::Char`: モードインジケーター（自律モードの場合は'A'）。
  * `valid::Bool`: データの有効性を示すフラグ。

# コンストラクタ

```julia
GLL(items::Array{D}; system::AbstractString = "UNKNOWN", valid = true) where D <: SubString
```

# 例

```julia
data = GLL(["GLL", "12.3456", "N", "98.7654", "W", "123456", "A"])
```
