```
function regress(f::StatsModels.FormulaTerm, df::DataFrames.AbstractDataFrame; α::Float64=0.05, req_stats=["default"], weights::Union{Nothing,String}=nothing,
remove_missing=false, cov=[:none], contrasts=nothing)

Estimate the coefficients of the regression, given a dataset and a formula. 

The formula details are provided in the StatsModels package and the behaviour aims to be similar as what the Julia GLM package provides.
The data shall be provided as a DataFrame without missing data.
If remove_missing is set to true a copy of the dataframe will be made and the row with missing data will be removed.
Some robust covariance estimator(s) can be requested through the `cov` argument.
Default contrast is dummy coding, other contrasts can be requested through the `contrasts` argument.
For a weighted regression, the name of column containing the analytical weights shall be identified by the `weights` argument.
```
