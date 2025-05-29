```
function regress(f::StatsModels.FormulaTerm, df::DataFrames.AbstractDataFrame; α::Float64=0.05, req_stats=["default"], weights::Union{Nothing,String}=nothing,
remove_missing=false, cov=[:none], contrasts=nothing)

データセットと式が与えられたときに回帰の係数を推定します。

式の詳細はStatsModelsパッケージで提供されており、その動作はJulia GLMパッケージが提供するものと似ています。
データは欠損データのないDataFrameとして提供される必要があります。
remove_missingがtrueに設定されている場合、データフレームのコピーが作成され、欠損データを含む行が削除されます。
いくつかのロバストな共分散推定器を`cov`引数を通じて要求することができます。
デフォルトのコントラストはダミーコーディングであり、他のコントラストは`contrasts`引数を通じて要求することができます。
加重回帰の場合、分析的重みを含む列の名前は`weights`引数によって特定される必要があります。
```
