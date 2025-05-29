```
orient_normals!(normals::Vector{<:AbstractVector}, points; k::Int=5)
```

表面上の法線の向きを修正します。これは、[compute_normals](@ref) 関数が法線が内向きか外向きかを保証しないためです。「無秩序な点からの表面再構築」- Hoppe (1992) のアプローチを使用しています。
