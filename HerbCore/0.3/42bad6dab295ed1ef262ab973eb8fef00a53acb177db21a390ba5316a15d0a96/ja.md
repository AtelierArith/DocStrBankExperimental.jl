```
@rulenode
```

[`RuleNode`](@ref)を短縮記法を使って構築します。[`RuleNode`](@ref)と[`AbstractHole`](@ref)は、[`Base.show`](@ref)を使用して表示されます。

[`HerbCore`](@ref)の外で定義された[`AbstractHole`](@ref)はまだサポートされていません。

!!! note "Holeドメインの表現"
    [`AbstractHole`](@ref)のドメインは、`Bool[...]`で囲まれて表示されます。このマクロは、`Bool[...]`の有無にかかわらずドメインを受け入れます：`UniformHole[Bool[1, 1, 0, 0]]{2,3}`と`UniformHole[1, 1, 0, 0]{2,3}`の両方が機能します。


# 例

```jldoctest
julia> @rulenode 1{4{5,6},1{2,3}}
1{4{5,6},1{2,3}}

julia> @rulenode 1
1

julia> @rulenode 1{2, 3}
1{2,3}

julia> @rulenode UniformHole[1, 1, 0, 0]{2,3}
UniformHole[Bool[1, 1, 0, 0]]{2,3}

julia> @rulenode Hole[1, 1, 0, 0]
Hole[Bool[1, 1, 0, 0]]

```
