```
PlotMatrix(Mat::AbstractMatrix, mle::AbstractVector; Confnum::Real=0., dims::Tuple{Int,Int}=(1,2), N::Int=400, plot::Bool=isloaded(:Plots), OverWrite::Bool=true, kwargs...)
```

与えられた共分散行列に対応する楕円をプロットします。これは、ベクトル `mle` によってオフセットされる場合があります。`Confnum` キーワード引数を介して与えられた行列の信頼レベルに関する情報を提供することにより、与えられた行列を適切に再スケールするための補正係数が計算されます。

例:

```
PlotMatrix(inv(FisherMetric(DM,mle)),mle)
```
