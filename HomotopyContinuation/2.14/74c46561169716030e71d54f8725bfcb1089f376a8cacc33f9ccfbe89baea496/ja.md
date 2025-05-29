```
search_in_radius(tree::VoronoiTree, v::AbstractVector, tol::Real)
```

与えられた `tree` に、`v` からの距離が最大 `tol` の点 `p` が含まれているかを検索します。点が存在しない場合は `nothing` を返し、そうでない場合は `p` の識別子が返されます。
