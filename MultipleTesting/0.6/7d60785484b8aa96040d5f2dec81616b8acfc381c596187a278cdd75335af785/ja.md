Beta-Uniform Mixture (BUM) π₀ 推定器

# 例

```jldoctest
julia> pvals = PValues([0.001, 0.002, 0.01, 0.03, 0.5]);

julia> estimate(pvals, BUM())
0.22802795505154264
```

# 参考文献

Pounds, S., and Morris, S.W. (2003). Estimating the occurrence of false positives and false negatives in microarray studies by approximating and partitioning the empirical distribution of p-values. Bioinformatics 19, 1236–1242.
