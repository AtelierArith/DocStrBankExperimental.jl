```
export_results(obs::Observable{T}[, filename::AbstractString, group::AbstractString; timeseries::Bool=false])
```

指定された可観測量の結果をJLDにきれいにエクスポートします。

名前、測定回数、平均および1シグマ誤差の推定値をエクスポートします。オプションで（`timeseries==true`）、完全な時系列もエクスポートします。
