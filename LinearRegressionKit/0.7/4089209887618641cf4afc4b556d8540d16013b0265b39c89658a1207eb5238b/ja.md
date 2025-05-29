```
function ridge(f::StatsModels.FormulaTerm, df::DataFrames.AbstractDataFrame, k::Float64 ; 
weights::Union{Nothing,String}=nothing, remove_missing=false, contrasts=nothing)

リッジ回帰は、kパラメータ（kとも呼ばれる）を期待します。
重みが提供されると、加重リッジ回帰の結果になります。
```
