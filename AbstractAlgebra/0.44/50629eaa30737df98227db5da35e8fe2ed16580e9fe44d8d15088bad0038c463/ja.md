```
polynomial_ring(R::NCRing, s::VarName = :x; cached::Bool = true)
```

基底環 `R` と生成子（変数）をどのように表示するかを指定するシンボル/文字列 `s` を与えると、新しい多項式環 $S = R[x]$ と環の生成子 $x$ を表すタプル `S, x` を返します。

デフォルトでは、親オブジェクト `S` は `R` と `x` のみ依存し、キャッシュされます。オプション引数 `cached` を `false` に設定すると、親オブジェクト `S` のキャッシュを防ぐことができます。

# 例

```jldoctest
julia> R, x = polynomial_ring(ZZ, :x)
(Univariate polynomial ring in x over integers, x)

julia> S, y = polynomial_ring(R, :y)
(Univariate polynomial ring in y over R, y)
```
