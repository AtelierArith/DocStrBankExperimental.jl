```
xcov(x::AbstractVecOrMat{<:Real}; demean::Bool=true, lags::AbstractVector{<:Integer}=Int[], maxlags=0)
```

ベクトルまたは行列 x の自己共分散を計算し、自己共分散を計算するラグをオプションで指定します。

x がベクトルの場合、lags と同じ長さのベクトルを返します。x が行列の場合、サイズが (length(lags), size(x,2)) の行列を返し、結果の各列は x の列に対応します。

出力は正規化されていません。正規化された関数については `xcorr` を参照してください。
