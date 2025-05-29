```
difference_of_convex_algorithm!(M, f, g, ∂h, p; kwargs...)
difference_of_convex_algorithm!(M, mdco, p; kwargs...)
```

凸の差分アルゴリズムを実行し、`p`の場所でステップを実行します。詳細については[`difference_of_convex_algorithm`](@ref)を参照してください。

[`ManifoldDifferenceOfConvexObjective`](@ref) `mdco`を指定した場合、`g`はキーワード引数です。
