```
polynomial_ring(R::Ring, varnames...; cached=true, internal_ordering=:lex)
polynomial_ring(R::Ring, varnames::Tuple; cached=true, internal_ordering=:lex)
```

[`polynomial_ring(::Ring, ::Vector{Symbol})`](@ref) と同様ですが、[`variable_names`](@ref) で指定されたように `varnames` を指定する方法が増えています。

`S, generators...` のタプルを返し、`generators[i]` は `varnames[i]` に対応します。

!!! note
    最初のメソッドでは、`varnames` は空であってはならず、もし1つの名前のみで構成されている場合は、単変数の [`polynomial_ring(R::NCRing, s::VarName)`](@ref) メソッドが呼び出されます。


# 例

```jldoctest
julia> S, (a, b, c) = polynomial_ring(ZZ, [:a, :b, :c])
(Multivariate polynomial ring in 3 variables over integers, AbstractAlgebra.Generic.MPoly{BigInt}[a, b, c])

julia> S, x, y = polynomial_ring(ZZ, :x => (1:2, 1:2), :y => 1:3);

julia> S
Multivariate polynomial ring in 7 variables x[1, 1], x[2, 1], x[1, 2], x[2, 2], ..., y[3]
  over integers

julia> x
2×2 Matrix{AbstractAlgebra.Generic.MPoly{BigInt}}:
 x[1, 1]  x[1, 2]
 x[2, 1]  x[2, 2]

julia> y
3-element Vector{AbstractAlgebra.Generic.MPoly{BigInt}}:
 y[1]
 y[2]
 y[3]
```
