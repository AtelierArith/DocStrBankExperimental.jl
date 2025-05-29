```
Dirichlet(u::Symbol, ∂Ω::AbstractVecOrSet, f::Function, components=nothing)
```

`∂Ω`の境界部分で`u`にDirichlet境界条件を作成します。`f`は`f(x)`または`f(x, t)`の形式の関数であり、`x`は空間座標、`t`は現在の時間で、指定された値を返します。`components`は、この条件によって指定される`u`の成分を指定します。デフォルトでは、`u`のすべての成分が指定されます。

集合`∂Ω`は、[`FacetIndex`](@ref)、[`FaceIndex`](@ref)、[`EdgeIndex`](@ref)、[`VertexIndex`](@ref)、または`Int`型の要素を持つ`AbstractSet`または`AbstractVector`であることができます。ほとんどの場合、要素型は`FacetIndex`です。単一の点を制約するには、`VertexIndex`を使用することが推奨されますが、特定のノードを`Int`要素を介してノード番号を指定することで制約することも可能です。例えば、3Dのエッジを制約するには、`EdgeIndex`要素を指定できます。

例えば、ここでは`∂Ω`と呼ばれるファセットセット上の`u`フィールドに対して`sin`関数によって与えられた値のDirichlet条件を作成します：

*例*

```jldoctest
# グリッドからファセットセットを取得
∂Ω = getfacetset(grid, "boundary-1")

# スカラー場:sを∂Ωでsin(t)に指定
dbc = Dirichlet(:s, ∂Ω, (x, t) -> sin(t))

# ベクトル場:vのすべての成分を∂Ωで0に指定
dbc = Dirichlet(:v, ∂Ω, x -> 0 * x)

# ベクトル場:vの成分2と3を∂Ωで[sin(t), cos(t)]に指定
dbc = Dirichlet(:v, ∂Ω, (x, t) -> [sin(t), cos(t)], [2, 3])
```

`Dirichlet`境界条件は、[`ConstraintHandler`](@ref)に追加され、[`apply!`](@ref)および/または[`apply_zero!`](@ref)を介して条件が適用されます。
