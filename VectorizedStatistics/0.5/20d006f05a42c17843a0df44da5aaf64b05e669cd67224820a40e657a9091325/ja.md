```julia
vcov(x::AbstractVector, y::AbstractVector; corrected::Bool=true, multithreaded=false)
```

ベクトル `x` と `y` の間の共分散を計算します。`Statistics.cov` と同様ですが、ベクトル化されており（オプションで）マルチスレッド対応です。

`corrected` が `true` の場合（デフォルト）、*ベッセルの補正* が適用され、合計は `n` ではなく `n-1` でスケーリングされます。ここで、`n = length(x)` です。
