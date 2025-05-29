ボンフェローニ調整

# 例

```jldoctest
julia> pvals = PValues([0.001, 0.01, 0.03, 0.5]);

julia> adjust(pvals, Bonferroni())
4-element Array{Float64,1}:
 0.004
 0.04
 0.12
 1.0

julia> adjust(pvals, 6, Bonferroni())
4-element Array{Float64,1}:
 0.006
 0.06
 0.18
 1.0
```

# 参考文献

Bonferroni, C.E. (1936). Teoria statistica delle classi e calcolo delle probabilita (Libreria internazionale Seeber).
