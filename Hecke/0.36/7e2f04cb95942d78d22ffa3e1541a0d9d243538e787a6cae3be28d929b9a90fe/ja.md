```
is_pure(U::FinGenAbGroup, G::FinGenAbGroup) -> Bool
```

部分群 `U` が `G` の純粋なものであるとは、すべての `n` に対して、`G` の乗法による `n` マップの像にある `U` の要素が `U` の要素の倍数でもある場合を指します。

有限アーベル群において、これは `U` が `G` に補群を持つことと同値です。これらはまた *孤立部分群* および *補助部分群* として知られています。

参照: [`is_neat`](@ref), [`has_complement`](@ref)

# 例

```julia
julia> G = abelian_group([2, 8]);

julia> U, _ = sub(G, [G[1]+2*G[2]]);

julia> is_pure(U, G)
false

julia> U, _ = sub(G, [G[1]+4*G[2]]);

julia> is_pure(U)
true

julia> has_complement(U, G)[1]
true
```
