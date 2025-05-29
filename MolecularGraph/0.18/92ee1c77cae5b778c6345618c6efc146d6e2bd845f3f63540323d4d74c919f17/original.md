```
all_maximal_conn_cliques(::Type{U}, g::SimpleGraph{T}, eattrs::Dict;
    kwargs...) where {T,U} -> (Vector{U}, Symbol)
```

Calculate maximal connected cliques.

# Reference

1. Cazals, F., & Karande, C. (2005). An algorithm for reporting maximal c-cliques. Theoretical Computer Science, 349(3), 484–490. https://doi.org/10.1016/j.tcs.2005.09.038
