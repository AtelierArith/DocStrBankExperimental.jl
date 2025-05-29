検閲されたベータ-一様混合（censored BUM）π₀推定量

# 例

```jldoctest
julia> pvals = PValues([0.001, 0.002, 0.01, 0.03, 0.5]);

julia> estimate(pvals, CensoredBUM())
0.21052495526400936

```

# 参考文献

Markitsis, A., and Lai, Y. (2010). A censored beta mixture model for the estimation of the proportion of non-differentially expressed genes. Bioinformatics 26, 640–646.
