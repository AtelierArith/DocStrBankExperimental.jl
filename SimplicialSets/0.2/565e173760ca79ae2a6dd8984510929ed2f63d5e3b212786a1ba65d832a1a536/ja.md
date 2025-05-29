```
LoopGroupSimplex{T<:AbstractSimplex} <: AbstractSimplex

LoopGroupSimplex(x::T) where T <: AbstractSimplex
```

この型は、型 `T` の要素を持つ単体的集合のカンループ群における単体を表します。後者の単体的集合は、次元 `0` の単体が1つだけ含まれていると仮定されており、これは縮小されていることを意味します。

コンストラクタは、単体 `x` によって決定されるループ群内の単体を返します。`x` は厳密に正の次元でなければなりません。

`LoopGroupSimplex{T}` を反復すると、そのコンポーネントが得られます。これらは型 `LoopGroupGenerator{T}` です。

関連情報は [`SimplicialSets.LoopGroupGenerator`](@ref) を参照してください。

# 例

```jldoctest
julia> using SimplicialSets: s, d

julia> x = SymbolicSimplex(:x, 2); y = LoopGroupSimplex(x)
⟨x[0,1,2]⟩

julia> d(y, 1), d(y, 0)
(⟨x[0,1]⟩, ⟨x[1,2]⁻¹,x[0,2]⟩)

julia> LoopGroupSimplex(s(x, 0))
⟨⟩
```
