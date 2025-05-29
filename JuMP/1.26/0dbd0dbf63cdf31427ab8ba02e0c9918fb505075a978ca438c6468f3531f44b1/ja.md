```
GenericAffExpr(constant::V, kv::AbstractArray{Pair{K,V}}) where {K,V}
```

定数とペアのベクターを渡すことで [`GenericAffExpr`](@ref) を作成します。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> GenericAffExpr(1.0, [x => 1.0])
x + 1
```
