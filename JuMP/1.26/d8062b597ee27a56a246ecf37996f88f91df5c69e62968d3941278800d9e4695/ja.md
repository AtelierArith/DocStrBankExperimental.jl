```
GenericQuadExpr(
    aff::GenericAffExpr{V,K},
    kv::AbstractArray{Pair{UnorderedPair{K},V}}
) where {K,V}
```

[`GenericQuadExpr`](@ref) を作成するには、[`GenericAffExpr`](@ref) と ([`UnorderedPair`](@ref), coefficient) ペアのベクトルを渡します。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> GenericQuadExpr(GenericAffExpr(1.0, x => 2.0), [UnorderedPair(x, x) => 3.0])
3 x² + 2 x + 1
```
