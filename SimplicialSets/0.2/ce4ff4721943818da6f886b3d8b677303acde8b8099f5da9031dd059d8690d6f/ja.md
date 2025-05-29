```
OppositeSimplex{T<:AbstractSimplex} <: AbstractSimplex
```

`OppositeSimplex(x)` は、`x` に対して「反対」の単体であり、`i` 番目の面演算子は `x` の `(n-i)` 番目の面演算子に対応し、退化演算子についても同様です。

引数の型が `OppositeSimplex` の関数 `*`、`\`、`inv` および `one` は、基礎となる単体に対して作用します。

`OppositeSimplex` の線形拡張は、単体集合のチェーン複体から反対の単体集合へのチェーン写像にはならないことに注意してください。この目的のために `opposite` 関数があります。

詳細は [`opposite`](@ref) を参照してください。

# 例

```jldoctest
julia> using SimplicialSets: d, s

julia> x = SymbolicSimplex(:x, 3)
x[0,1,2,3]

julia> y = OppositeSimplex(x)
OppositeSimplex(x[0,1,2,3])

julia> d(y, 1)
OppositeSimplex(x[0,1,3])

julia> s(y, 1)
OppositeSimplex(x[0,1,2,2,3])

julia> z = OppositeSimplex(LoopGroupSimplex(x))
OppositeSimplex(⟨x[0,1,2,3]⟩)

julia> inv(z)
OppositeSimplex(⟨x[0,1,2,3]⁻¹⟩)
```
