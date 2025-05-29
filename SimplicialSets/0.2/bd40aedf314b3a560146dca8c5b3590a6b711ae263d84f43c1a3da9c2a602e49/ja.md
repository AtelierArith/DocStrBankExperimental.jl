```
opposite(a::AbstractLinear{T,R}) -> Linear
```

`a`の項に`opposite`を適用し、それらの線形結合を返します。項`x`の次数が`4`で`1`または`2`の合同である場合、それは`-opposite(x)`に変換され、それ以外の場合は`opposite(x)`に変換されます。

この関数は`opposite(x::AbstractSimplex)`または`OppositeSimplex`の線形拡張ではないことに注意してください。符号は、この関数が項`x`を含む単体集合の鎖複体から反対の単体集合への鎖写像であるように選ばれています。

[`opposite(::AbstractSimplex)`](@ref)や[`opposite(::AbstractTensor)`](@ref)も参照してください。

# 例

```jldoctest
julia> using LinearCombinations; using LinearCombinations: diff

julia> a = Linear(SymbolicSimplex(:x, 1) => 2)
Linear{SymbolicSimplex{Symbol}, Int64} with 1 term:
2*x[0,1]

julia> b = opposite(a)
Linear{OppositeSimplex{SymbolicSimplex{Symbol}}, Int64} with 1 term:
-2*OppositeSimplex(x[0,1])

julia> diff(b) == opposite(diff(a))
true

julia> c = Linear(OppositeSimplex(y) => c for (y, c) in a)
Linear{OppositeSimplex{SymbolicSimplex{Symbol}}, Int64} with 1 term:
2*OppositeSimplex(x[0,1])

julia> diff(c) == opposite(diff(a))
false
```
