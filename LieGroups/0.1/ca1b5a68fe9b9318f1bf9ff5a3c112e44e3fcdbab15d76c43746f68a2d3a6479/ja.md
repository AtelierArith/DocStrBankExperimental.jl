```
cross(G::LieGroup, H::LieGroup)
G × H
G1 × G2 × G3 × ...
```

Return the [`ProductLieGroup`](@ref) For two [`LieGroups`](@ref) `G` and `H`、一方が[`ProductLieGroup`](@ref)である場合、もう一方は（`H`が積の場合は前に、`G`が積の場合は後ろに）追加されます。両方が積リー群である場合、それらは操作の順序を保持しながら一つに結合されます。

二つ以上が`×`で連結される場合、この処理は繰り返されます。
