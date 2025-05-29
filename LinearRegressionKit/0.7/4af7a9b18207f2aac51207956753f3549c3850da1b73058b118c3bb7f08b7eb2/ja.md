```
function regress(f::StatsModels.FormulaTerm, df::AbstractDataFrame, req_plots; α::Float64=0.05, req_stats=["default"], weights::Union{Nothing,String}=nothing, remove_missing=false, cov=[:none], contrasts=nothing, plot_args=Dict("plot_width" => 400, "loess_bw" => 0.6, "residuals_with_density" => false))

回帰の係数を推定し、データセットと式を与え、要求されたプロットを提供します。
生成されたプロットの辞書は、プロットの説明によってインデックス付けされています。

プロットの幅やLoessスムーザーのバンド幅を指定することが可能です。
```
