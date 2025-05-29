```
function ridge(f::StatsModels.FormulaTerm, df::DataFrames.AbstractDataFrame, ks::AbstractRange ; 
weights::Union{Nothing,String}=nothing, remove_missing=false, contrasts=nothing, traceplots=false)

リッジ回帰は、kパラメータの範囲（kとも呼ばれる）を期待します。
重みが提供されると、加重リッジ回帰の結果になります。
トレースプロットが要求されると、トレースプロットの辞書も返します。
```
