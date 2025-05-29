```julia
get_mpm_partition(eq_probs::AbstractMatrix) -> Any
get_mpm_partition(
    eq_probs::AbstractMatrix,
    threshhold
) -> Any

```

中央値の事後確率モデル/パーティションを計算します。これは回帰における中央値モデル/パーティションとは異なることに注意してください。パーティションの場合、`sum(abs2(eq_probs[i, j] - (p[i] == p[j])) for i in eachindex(p), j in eachindex(p))` を最小化するパーティション `p` を見つけます。これはヒューリスティックな方法で行われるため、結果が真のmpmであることは保証されません。
