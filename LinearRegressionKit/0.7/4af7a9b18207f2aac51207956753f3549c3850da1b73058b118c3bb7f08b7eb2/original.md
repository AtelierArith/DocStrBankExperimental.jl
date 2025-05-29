```
function regress(f::StatsModels.FormulaTerm, df::AbstractDataFrame, req_plots; α::Float64=0.05, req_stats=["default"], weights::Union{Nothing,String}=nothing, remove_missing=false, cov=[:none], contrasts=nothing, plot_args=Dict("plot_width" => 400, "loess_bw" => 0.6, "residuals_with_density" => false))

Estimate the coefficients of the regression, given a dataset and a formula. and provide the requested plot(s).
A dictionary of the generated plots indexed by the descritption of the plots.

It is possible to indicate the width of the plots, and the bandwidth of the Loess smoother.
```
