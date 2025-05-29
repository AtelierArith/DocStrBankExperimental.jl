```
centrality_katz(N::Unipartite; a::Float64=0.1, k::Int64=5)
```

この指標は異なるパスの長さ（`k`）で機能し、すべての後続の接続に異なる重み（`a`）を与えます。`k`は少なくとも1でなければなりません（直接の隣接者のみが考慮されます）。`a`（重みであるため）は正でなければなりません。

> Katz, L., 1953. A new status index derived from sociometric analysis. Psychometrika 18, 39–43. doi:10.1007/bf02289026

