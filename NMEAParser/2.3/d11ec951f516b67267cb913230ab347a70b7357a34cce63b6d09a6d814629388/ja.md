```
struct RMC <: NMEAString
```

推奨最小航法情報 (RMC)

このNMEAデータ型は、推奨される最小航法情報を表します。

# フィールド

  * `system::String`: GNSSシステム識別子（例：GPS、GLONASS、GALILEO、組み合わせ）。
  * `time::Float64`: 位置修正の秒数。
  * `status::Bool`: ステータスインジケーター（アクティブな場合はtrue、そうでない場合はfalse/無効）。
  * `latitude::Float64`: 緯度（小数度）。
  * `longitude::Float64`: 経度（小数度）。
  * `sog::Float64`: 地上速度（ノット）。
  * `cog::Float64`: 地上のトラック角度（度）。
  * `date::Date`: 月の日。
  * `month::String`: 年の月。
  * `year::String`: 年。
  * `magvar::Float64`: 磁気偏差。
  * `mode::Char`: 位置システムモードインジケーター（D=差分、A=自律、N=無効、E=推定/死角、M=手動入力）。
  * `navstatus::Char`: 航法ステータス。（S = 安全、C = 注意、U = 安全でない、V = 航法ステータスが無効）。
  * `valid::Bool`: データの有効性を示すフラグ。

# コンストラクタ

```julia
RMC(items::Array{D}; system::AbstractString = "UNKNOWN", valid = true) where D <: SubString
```

# 例

```julia
nmeastr = "$GPRMC,123519,A,4807.038,N,01131.000,E,022.4,084.4,230394,003.1,W*6A"
data = RMC(["RMC", "123519", "A", "4807.038", "N", "01131.000", "E", "022.4", "084.4", "230394", "003.1", "W"], "GPS", true)

altstr = "$GNRMC,060512.00,A,3150.788156,N,11711.922383,E,0.0,,311019,,,A,V*1B"
```
