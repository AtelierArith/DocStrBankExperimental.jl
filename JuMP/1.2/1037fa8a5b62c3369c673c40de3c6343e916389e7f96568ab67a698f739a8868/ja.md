```
GenericAffExpr(constant::V, kv::Vararg{Pair{K,V},N}) where {K,V,N}
```

定数と追加の引数のペアを渡すことで [`GenericAffExpr`](@ref) を作成します。

## 例

```jldoctest; setup=:(using JuMP; model = Model(); @variable(model, x)) julia> GenericAffExpr(1.0, x => 1.0) x + 1

```
