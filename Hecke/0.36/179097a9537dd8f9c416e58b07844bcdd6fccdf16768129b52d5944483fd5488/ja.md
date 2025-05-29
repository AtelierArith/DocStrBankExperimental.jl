```
is_neat(U::FinGenAbGroup, G::FinGenAbGroup) -> Bool
```

部分群 `U` が `G` の neat であるとは、すべての素数 `p` に対して、`G` の `p` 乗算写像の像にある `U` の要素が、`U` の要素の倍数でもある場合を指します。

参照: [`is_pure`](@ref)

# 例

```julia
julia> G = abelian_group([2, 8]);

julia> U, _ = sub(G, [G[1] + 2*G[2]]);

julia> is_neat(U, G)
true

julia> is_pure(U, G)
false
```
