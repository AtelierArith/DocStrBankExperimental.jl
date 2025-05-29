```julia
nancovem(X::AbstractMatrix; dims::Int=1, corrected::Bool=true)
```

NaNを無視して、次元`dims`に沿った行列`X`の平均の誤差の共分散行列を計算します。つまり、行列`X`の各列（dims=1）または行（dims=2）の非NaNペアの平均の誤差の共分散で構成された行列です。平均の誤差の共分散は、標準誤差が標準偏差に対するように共分散に対応します。

`corrected`が`true`（デフォルト）である場合、*ベッセルの補正*が適用され、合計は`n`ではなく`n-1`でスケーリングされます。ここで、`n = length(x)`です。
