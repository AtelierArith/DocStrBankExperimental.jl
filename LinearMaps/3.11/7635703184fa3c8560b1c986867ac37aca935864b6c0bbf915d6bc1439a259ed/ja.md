```
*(A::LinearMap, X::Union{AbstractMatrix,AbstractQ})::CompositeMap
```

`CompositeMap` `A*LinearMap(X)`を返します。行列`X`を列ベクトルの集合ではなく線形演算子として解釈します。`A`が`X`の各列に作用する計算を行うには、`Matrix(A*X)`を呼び出すか、適切なサイズの事前に確保された行列`Y`を使って`mul!(Y, A, X[, α, β])`を使用します。

## 例

```jldoctest; setup=(using LinearMaps)
julia> A=LinearMap([1.0 2.0; 3.0 4.0]); X=[1.0 1.0; 1.0 1.0];

julia> A*X isa LinearMaps.CompositeMap
true
```
