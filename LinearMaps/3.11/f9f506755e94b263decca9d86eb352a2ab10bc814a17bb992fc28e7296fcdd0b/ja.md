```
*(X::Union{AbstractMatrix,AbstractQ}, A::LinearMap)::CompositeMap
```

`CompositeMap` `LinearMap(X)*A` を返します。行列 `X` を線形演算子として解釈します。`A` の `X` の各行に対する右作用を計算するには、`Matrix(X*A)` またはインプレースバージョンの `mul!(Y, X, A)` を呼び出します。

## 例

```jldoctest; setup=(using LinearMaps)
julia> X=[1.0 1.0; 1.0 1.0]; A=LinearMap([1.0 2.0; 3.0 4.0]);

julia> X*A isa LinearMaps.CompositeMap
true
```
