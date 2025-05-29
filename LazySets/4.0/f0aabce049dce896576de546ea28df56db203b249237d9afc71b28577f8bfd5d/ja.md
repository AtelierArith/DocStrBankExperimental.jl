# 拡張ヘルプ

```
linear_map(M::AbstractMatrix, P::LazySet; kwargs...)
```

### アルゴリズム

デフォルトの実装は、`P` が多面体であると仮定し、セットタイプに基づいたアルゴリズムを適用します（[`_linear_map_polyhedron`](@ref）を参照）。
