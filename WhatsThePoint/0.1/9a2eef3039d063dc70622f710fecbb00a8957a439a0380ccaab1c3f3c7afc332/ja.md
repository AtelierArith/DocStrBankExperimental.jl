```
orient_normals!(search_method::KNearestSearch, normals::AbstractVector{<:AbstractVector}, points)
```

サーフェス上の法線の向きを修正します。これは、[compute_normals](@ref) 関数が法線が内向きか外向きかを保証しないためです。「無秩序な点からのサーフェス再構築」- Hoppe (1992) のアプローチを使用します。
