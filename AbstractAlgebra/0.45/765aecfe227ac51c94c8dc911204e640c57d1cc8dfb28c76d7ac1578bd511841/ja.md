```
universal_polynomial_ring(R::Ring, varnames::Vector{Symbol}; cached::Bool=true, internal_ordering::Symbol=:lex)
universal_polynomial_ring(R::Ring; cached::Bool=true, internal_ordering::Symbol=:lex)
```

係数環 `R` と変数名、例えば `varnames = [:x1, :x2, ...]` を与えると、普遍多項式環 `S = R[x1, x2, \dots]` とその生成元 `x1, x2, \dots` のタプル `S, [x1, x2, ...]` を返します。

`varnames` が省略された場合、初めは変数を持たない普遍多項式環 `S = R[\ldots]` を表すオブジェクトを返します。

# 例

```jldoctest
julia> S, (x,y) = universal_polynomial_ring(ZZ, [:x,:y])
(Universal Polynomial Ring over Integers, AbstractAlgebra.Generic.UnivPoly{BigInt}[x, y])

julia> z = gen(S, :z)
z

julia> x*y - z
x*y - z

julia> S = universal_polynomial_ring(ZZ)
Universal Polynomial Ring over Integers

julia> x = gen(S, :x)
x

julia> y, z = gens(S, [:y, :z])
2-element Vector{AbstractAlgebra.Generic.UnivPoly{BigInt}}:
 y
 z

julia> x*y - z
x*y - z
```
