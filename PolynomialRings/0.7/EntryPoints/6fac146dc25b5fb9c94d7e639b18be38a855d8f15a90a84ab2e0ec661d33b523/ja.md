```
polynomial_ring(symbols::Symbol...; basering=Rational{BigInt}, exptype=Int16, monomialorder=:degrevlex)
```

`basering` の変数名で指定された `symbols` の上の多項式環の型を作成し、型とこれらの変数のタプルを返します。

`exptype` パラメータは指数の整数型を定義します。

`monomialorder` は、例えばグレブナー基底計算のための単項式の順序を定義します。また、内部のソート順序も定義します。組み込みの値は `:degrevlex`、 `:deglex` および `:lex` です。この関数は任意のシンボルを受け入れますが、次のようにして独自の単項式順序を実装することができます。

```
Base.Order.lt(::MonomialOrder{:myorder}, a::M, b::M) where M <: AbstractMonomial
```

例については `PolynomialRings.MonomialOrderings` を参照してください。

# 例

```jldoctest
julia> using PolynomialRings

julia> R,(x,y,z) = polynomial_ring(:x, :y, :z);

julia> x*y + z
x*y + z
```
