```
all_maximal_conn_cliques(::Type{U}, g::SimpleGraph{T}, eattrs::Dict;
    kwargs...) where {T,U} -> (Vector{U}, Symbol)
```

最大接続クリークを計算します。

# 参考文献

1. Cazals, F., & Karande, C. (2005). 最大 c-クリークを報告するためのアルゴリズム. 理論計算機科学, 349(3), 484–490. https://doi.org/10.1016/j.tcs.2005.09.038
