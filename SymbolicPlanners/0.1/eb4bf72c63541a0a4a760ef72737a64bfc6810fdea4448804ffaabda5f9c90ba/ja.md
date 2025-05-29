```julia
BiAStarPlanner(f_heuristic, b_heuristic; kwargs...)

```

双方向A*探索で、`f_heuristic`は前方探索のヒューリスティックであり、`b_heuristic`は後方探索のヒューリスティックです。`kwargs`として指定されたオプションは、後方探索と前方探索の両方で共有されます。
