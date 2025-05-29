高次批判閾値

# 例

```jldoctest
julia> pvals = PValues([0.001, 0.01, 0.03, 0.5]);

julia> estimate(pvals, HigherCriticismThreshold())
0.03
```

# 参考文献

Donoho, D., and Jin, J. (2008). 高次批判閾値処理: 有用な特徴が稀で弱いときの最適特徴選択. PNAS 105, 14790–14795.

Klaus, B., and Strimmer, K. (2013). 稀で弱い特徴の信号識別: 高次批判または偽発見率? Biostatistics 14, 129–143.
