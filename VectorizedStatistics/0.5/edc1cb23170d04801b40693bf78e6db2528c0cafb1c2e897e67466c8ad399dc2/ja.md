```julia
vcov(X::AbstractMatrix; dims::Int=1, corrected::Bool=true, multithreaded=false)
```

行列 `X` の共分散行列を次元 `dims` に沿って計算します。`Statistics.cov` と同様ですが、ベクトル化されており（オプションで）マルチスレッド対応です。

`corrected` が `true`（デフォルト）である場合、*ベッセルの補正* が適用され、合計は `n` ではなく `n-1` でスケーリングされます。ここで、`n = length(x)` です。
