```
struct VTG <: NMEAString
```

トラックメイドグッドとグラウンドスピード (VTG)

このNMEAデータタイプは、トラックメイドグッド（コース）とグラウンドスピードに関する情報を表します。

# フィールド

  * `system::String`: GNSSシステム識別子（例：GPS、GLONASS、GALILEO、組み合わせ）。
  * `CoG_true::Float64`: 真の度数での地上コース。
  * `CoG_mag::Float64`: 磁気度数での地上コース。
  * `SoG_knots::Float64`: ノットでの地上スピード。
  * `SoG_kmhr::Float64`: 時速キロメートルでの地上スピード。
  * `mode::Char`: モードインジケーター（自律モードの場合は'A'）。
  * `valid::Bool`: データの有効性を示すフラグ。

# コンストラクタ

```julia
VTG(items::Array{D}; system::AbstractString = "UNKNOWN", valid = true) where D <: SubString
```

# 例

```julia
data = VTG(["VTG", "90.0", "T", "45.0", "M", "5.0", "K", "A"])
```
