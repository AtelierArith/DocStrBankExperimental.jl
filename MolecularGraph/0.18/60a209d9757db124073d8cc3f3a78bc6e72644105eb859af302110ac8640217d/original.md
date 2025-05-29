```
all_maximal_cliques(::Type{U}, g::SimpleGraph{T}; kwargs...
    ) where {T,U} -> (Vector{U}, Symbol)
```

Calculate maximal cliques.

# Reference

1. Tomita, E., Tanaka, A., & Takahashi, H. (2006). The worst-case time complexity for generating all maximal cliques and computational experiments. Theoretical Computer Science, 363(1), 28–42. https://doi.org/10.1016/J.TCS.2006.06.015
2. Cazals, F., & Karande, C. (2008). A note on the problem of reporting maximal cliques. Theoretical Computer Science, 407(1–3), 564–568. https://doi.org/10.1016/j.tcs.2008.05.010
