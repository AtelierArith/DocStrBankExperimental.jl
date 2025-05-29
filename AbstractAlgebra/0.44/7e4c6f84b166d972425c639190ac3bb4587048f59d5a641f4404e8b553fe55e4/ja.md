```
polynomial_ring(R::Ring, varnames::Vector{Symbol}; cached=true, internal_ordering=:lex)
```

係数環 `R` と変数名、例えば `varnames = [:x1, :x2, ...]` を与えると、$S = R[x1, x2, \dots]$ の多項式環とその生成元 $x1, x2, \dots$ のタプル `S, [x1, x2, ...]` を返します。

デフォルトでは（`cached=true`）、出力 `S` はキャッシュされます。つまり、同じ引数で `polynomial_ring` が再度呼び出されると、同じ（*同一の*）環が返されます。`cached` を `false` に設定すると、異なる新しい環が返され、キャッシュされることも防ぎます。

`S` 内の多項式の内部ストレージに使用される単項式順序は `internal_ordering` で設定でき、`:lex`、`:deglex` または `:degrevlex` のいずれかでなければなりません。

関連情報: [`polynomial_ring(::Ring, ::Vararg)`](@ref)、[`@polynomial_ring`](@ref)。

# 例

```jldoctest
julia> S, generators = polynomial_ring(ZZ, [:x, :y, :z])
(Multivariate polynomial ring in 3 variables over integers, AbstractAlgebra.Generic.MPoly{BigInt}[x, y, z])
```
