```julia
nancov(X::AbstractMatrix; dims::Int=1, corrected::Bool=true)
```

行列 `X` の共分散行列を次元 `dims` に沿って計算します。`Statistics.cov` と同様ですが、`NaN` を無視します。

`corrected` が `true` の場合（デフォルト）、*ベッセルの補正* が適用され、合計は `n` ではなく `n-1` でスケーリングされます。ここで、`n = length(x)` です。
