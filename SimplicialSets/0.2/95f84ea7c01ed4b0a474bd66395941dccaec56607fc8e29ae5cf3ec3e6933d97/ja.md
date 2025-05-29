```
BarSimplex{T} <: AbstractSimplex

BarSimplex(iter; op::Union{typeof(*),typeof(+)} = *) -> BarSimplex
```

バースンプルックスを表す型。`T`が`AbstractSimplex`のサブタイプである場合、それは単体群であると仮定されます。そうでない場合、`T`は乗法的離散群であると仮定されます。

コンストラクタはバースンプルックスのコンポーネントに対するイテレータを受け取ります。オプションのキーワード`op`は、群が乗法的（デフォルト）か加法的かを示します。

`BarSimplex`を反復することは、そのコンポーネントを反復することを意味します。

詳細は[`AddToMul`](@ref)を参照してください。

# 例

```jldoctest
julia> using SimplicialSets: d, s

julia> b = BarSimplex([Lattice(1, 2), Lattice(3, 4)]; op = +)
[(1, 2),(3, 4)]

julia> d(b, 0)
[(3, 4)]

julia> d(b, 1)
[(4, 6)]

julia> s(b, 1)
[(1, 2),(0, 0),(3, 4)]

julia> collect(b)
2-element Vector{AddToMul{Lattice{2}}}:
 (1, 2)
 (3, 4)

julia> b1 = BarSimplex([Lattice(1, 2)]; op = +)
[(1, 2)]

julia> b0 = BarSimplex(Lattice{2}[]; op = +)
[]

julia> c = BarSimplex([b0, b1])
[[],[(1, 2)]]

julia> s(c, 1)
[[],[(0, 0)],[(0, 0),(1, 2)]]
```
