```julia
logsumexp(X; dims)

```

`log.(sum(exp.(X); dims=dims))`を計算します。

結果は、データに対して1回のパスを使用して、中間的なオーバーフローおよびアンダーフローを回避する数値的に安定した方法で計算されます。

[`logsumexp!`](@ref)も参照してください。

# 参考文献

[Sebastian Nowozin: Streaming Log-sum-exp Computation](http://www.nowozin.net/sebastian/blog/streaming-log-sum-exp-computation.html)
