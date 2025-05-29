```
AutoAlgorithm{T, M <: Manifold}(manifold::M, x::T)
```

は、渡された多様体（[`AutoManifold`](@ref) である可能性があります）とデータ `x` に基づいて、[`Operation`](@ref) が入力データに対して最適なアルゴリズムを自動的に選択する必要があることを示します。

実際の実装は、その特定の [`Operation`](@ref) の実装に委ねられています。
