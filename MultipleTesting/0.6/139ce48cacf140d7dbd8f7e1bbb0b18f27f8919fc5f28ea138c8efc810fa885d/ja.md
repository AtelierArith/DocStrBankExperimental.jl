Logit p-value 組み合わせ

# 例

```jldoctest
julia> pvals = PValues([0.01, 0.02, 0.3, 0.5]);

julia> combine(pvals, Logit())
0.006434494635148462
```

# 参考文献

Mudholkar, G.S., and George, E.O. (1977). The Logit Statistic for Combining Probabilities - An Overview (Rochester University NY, Dept of Statistics).
