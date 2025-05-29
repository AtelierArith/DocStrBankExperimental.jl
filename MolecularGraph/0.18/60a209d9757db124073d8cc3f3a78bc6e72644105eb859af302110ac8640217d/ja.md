```
all_maximal_cliques(::Type{U}, g::SimpleGraph{T}; kwargs...
    ) where {T,U} -> (Vector{U}, Symbol)
```

最大クリークを計算します。

# 参考文献

1. Tomita, E., Tanaka, A., & Takahashi, H. (2006). 最大クリークを生成するための最悪ケースの時間計算量と計算実験. 理論計算機科学, 363(1), 28–42. https://doi.org/10.1016/J.TCS.2006.06.015
2. Cazals, F., & Karande, C. (2008). 最大クリークを報告する問題に関するノート. 理論計算機科学, 407(1–3), 564–568. https://doi.org/10.1016/j.tcs.2008.05.010
