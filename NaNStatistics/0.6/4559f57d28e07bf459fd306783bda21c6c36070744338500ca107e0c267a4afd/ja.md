```julia
nancovem(x::AbstractVector, y::AbstractVector; corrected::Bool=true)
```

`x` と `y` の非ナンペアの平均の誤差の共分散を計算します。平均の誤差の共分散は、平均の標準誤差が標準偏差に対するように、共分散に対するものです。

`corrected` が `true` の場合（デフォルト）、*ベッセルの補正* が共分散に適用され、合計は `n` ではなく `n-1` でスケーリングされます。ここで、`n = length(x)` です。
