```
bacterialblight(wth::DataFrames.AbstractDataFrame, emergence::Dates.Date)
```

天候データと米の細菌性斑点病 *Xanthomonas oryzae* pv. *oryzae* の最適曲線値を使用して、健康-潜伏-感染-感染後（HLIP）モデルを実行します。

## 引数

  * `wth::DataFrames.AbstractDataFrame`: 以下の値を含む日次の天候データ。

      * `YYYYMMDD::Union{AbstractString, Dates.Date}`: ISO8601形式の日付、*すなわち*、YYYY-MM-DD
      * `DOY::Int64`: 年の連続日、一般に「ユリウス日」と呼ばれる
      * `TEMP::AbstractFloat`: 平均日温度 (°C)
      * `RHUM::AbstractFloat`: 平均日相対湿度 (%)
      * `RAIN::AbstractFloat`: 平均日降雨量 (mm)
  * `emergence::Union{AbstractString, Dates.Date}`: 植物の出現が期待される日付。表1 Savary *et al.* 2012より。
  * `duration::Int64`: シミュレーションの期間（成長期の長さ、日数）、デフォルトは120日（Savary *et al.* 2012に従う）。表1 Savary *et al.* 2012より。

## 戻り値

細菌性斑点病の重症度に関する予測を含む `DataFrames.DataFrame`。入力された天候データに緯度と経度が含まれている場合、マッピング目的でそれらも含まれます。戻り値の完全な説明については [`hlipmodel`](@ref) を参照してください。

## 注意事項

これはヘルパー関数のファミリーの一つです。他にも [`brownspot`](@ref)、[`leafblast`](@ref)、[`sheathblight`](@ref) および [`tungro`](@ref) を参照してください。

## 例

```julia
julia> using Epicrop

julia> using DelimitedFiles

julia> using DataFrames

julia> data, header = readdlm(joinpath(
                                dirname(pathof(Epicrop)),
                                    "..", "docs", "src", "assets",
                                        "POWER_data_LB_PHI_2000_ws.csv"),
                                ',', header=true)

julia> w = DataFrame(data, vec(header))

julia> emergence = "2000-07-01"

julia> bacterialblight(w, emergence)
```
