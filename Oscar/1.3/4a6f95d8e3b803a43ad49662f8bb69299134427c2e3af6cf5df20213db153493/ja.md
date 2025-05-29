```
PcGroupElem
```

多項群の要素。

多項群の生成元は `f1`、`f2`、`f3` などとして表示され、すべての多項群の要素は生成元の積として表示されます。

# 例

```jldoctest
julia> G = abelian_group(PcGroup, [2, 3]);

julia> G[1], G[2]
(f1, f2)

julia> G[2]*G[1]
f1*f2
```

これは `f1`、`f2` などの名前のJulia変数を定義するものではありません！群 `G` の生成元を取得するには `gens(G)` を使用してください。便利のために、`G[1]`、`G[2]` としてもアクセスできます。これはセクション [Elements of groups](@ref elements_of_groups) に示されています。
