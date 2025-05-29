```
y, A = circulant_mh_attention(simfun::AbstractSimilarity, q, k, v, W::Int, nheads::Int)
```

循環マルチヘッドアテンションを実行します。つまり、`nheads`グループの循環アテンションを個別に実行し、結果をチャネルに沿って連結します。`q`、`k`、`v`のチャネル数は`nheads`で割り切れる必要があります。返される隣接行列`A`は`size(A, 3) == nheads`になります。

[`circulant_attention`](@ref)、[`DotSimilarity`](@ref)、[`DistanceSimilarity`](@ref)も参照してください。
