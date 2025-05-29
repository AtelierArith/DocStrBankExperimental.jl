```
+(A::LinearMap, B::LinearMap)::LinearCombination
```

2つの演算子の和/線形結合の（遅延）表現を構築します。`LinearMap`/`LinearCombination`オブジェクトの和と`LinearMap`/`LinearCombination`オブジェクトの和は、単一の`LinearCombination`に簡約されます。`LinearMap`と`AbstractMatrix`/`UniformScaling`オブジェクトの和では、後者が自動的に`LinearMap`に昇格されます。

# 例

```jldoctest; setup=(using LinearAlgebra, LinearMaps)
julia> CS = LinearMap{Int}(cumsum, 3)::LinearMaps.FunctionMap;

julia> LinearMap(ones(Int, 3, 3)) + CS + I + rand(3, 3);
```
