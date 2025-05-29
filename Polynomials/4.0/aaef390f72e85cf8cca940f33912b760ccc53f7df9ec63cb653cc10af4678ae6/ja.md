```
AbstractPolynomial{T,X}
```

さまざまな多項式のための抽象型で、*暗黙の* 基底を持っています。

多項式型は、変数 `X` を保持し、型 `T` の係数をいくつかのコンテナ型に格納し、標準基底のような暗黙の基底を持っています。

# 特性

  * `coeffs` - 多項式の係数

# 型 `T`

`T` は `T <: Number` である必要はなく、現時点では制限されていません。

いくつかの `T` は成功しないでしょう。

  * スカラー乗算: `c::Number * p::Polynomial` は定義されるべきです。
  * スカラー乗算: `c::T * p::Polynomial{T}` は `T <: AbstractPolynomial` の場合に曖昧さがあります。
  * スカラー乗算: `p::Polynomial{T} * c::T` は必ずしも可換ではありません。
  * 加算/減算: `p::Polynomial{T} + q::Polynomial{T}` は定義されるべきです。
  * 減算: `p - p` は時々 `zero{T}` が定義される必要があります。
  * 多項式乗算: `p::Polynomial{T} * q::Polynomial{T}` は "`T * T`" が定義される必要があります（例: `Base.promote_op(*, Vector{Int}, Vector{Int})` は何かである必要があります）。
  * 多項式の累乗: `p::Polynomial{T}^2` は "`T^2`" が定義される必要があります。
  * 暗黙の昇格: `p::Polynomial{T} + c::Number` は `convert(T, c)` が定義される必要があります。
  * 暗黙の昇格: `p::Polynomial{T} + c::T` は `T <: AbstractPolynomial` の場合に曖昧さがあります。
  * 評価: `p::Polynomial{T}(s::Number)`
  * 評価 `p::Polynomial{T}(c::T)` は `T*T` が定義される必要があります。
  * `0` 多項式の評価には `zero(T)` が定義される必要があります。
  * 微分: `derivative(p::Polynomial{T})`
  * 積分: `integrate(p::Polynomial{T})`
