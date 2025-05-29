```
@polynomial_ring(R::Ring, varnames...; cached=true, internal_ordering=:lex)
```

[`polynomial_ring(::Ring, ::Vararg)`](@ref) から多項式環を返し、生成子を現在のスコープに導入します。

# 例

```jldoctest
julia> S = @polynomial_ring(ZZ, "x#" => (1:2, 1:2), "y#" => 1:3)
7変数 x11, x21, x12, x22, ..., y3 の多変数多項式環
  整数上

julia> x11, x21, x12, x22
(x11, x21, x12, x22)

julia> y1, y2, y3
(y1, y2, y3)

julia> (S, [x11 x12; x21 x22], [y1, y2, y3]) == polynomial_ring(ZZ, "x#" => (1:2, 1:2), "y#" => 1:3)
true
```
