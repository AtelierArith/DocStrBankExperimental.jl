```julia
logsumexp!(out, X)

```

`X`の[`logsumexp`](@ref)を`out`の単一次元にわたって計算し、結果を`out`に書き込みます。

結果は、データに対して1回のパスを使用して、中間的なオーバーフローおよびアンダーフローを回避する数値的に安定した方法で計算されます。

[`logsumexp`](@ref)も参照してください。

# 参考文献

[Sebastian Nowozin: Streaming Log-sum-exp Computation](http://www.nowozin.net/sebastian/blog/streaming-log-sum-exp-computation.html)
