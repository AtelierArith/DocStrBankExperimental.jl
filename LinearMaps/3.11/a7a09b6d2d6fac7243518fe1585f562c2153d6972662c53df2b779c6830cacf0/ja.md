```
*(A::LinearMap, B::LinearMap)::CompositeMap
```

二つの演算子の積の（遅延）表現を構築します。`LinearMap`/`CompositeMap`オブジェクトと`LinearMap`/`CompositeMap`オブジェクトの積は、単一の`CompositeMap`に簡略化されます。`LinearMap`と`AbstractMatrix`/`UniformScaling`オブジェクトの積では、後者が自動的に`LinearMap`に昇格されます。

# 例

```jldoctest; setup=(using LinearAlgebra, LinearMaps)
julia> CS = LinearMap{Int}(cumsum, 3)::LinearMaps.FunctionMap;

julia> LinearMap(ones(Int, 3, 3)) * CS * I * rand(3, 3);
```
