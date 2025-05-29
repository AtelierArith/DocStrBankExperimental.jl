```
PiecewiseFunction([parity::Symbol,] pieces::Vector{Piece})
```

`PiecewiseFunction`のコンストラクタ。オプションの引数`parity`は`:none`（デフォルト）、`:even`、または`:odd`です。引数`pieces`はさまざまな部分を含みます（[`Piece`](@ref)を参照）。

## フィールド

  * `parity::Symbol`
  * `pieces::Vector{Piece}`

## 例

これは$1/x$のコーシー主値を表します：

```julia-repl
julia> f = PiecewiseFunction(:odd, Piece((0, Inf), (false, true), x -> 1 / x))
< Piecewise odd function with 1 piece and support [-Inf, Inf] >

julia> f.([-1, 0, 1])
3-element Vector{Real}:
 -1.0
  0
  1.0

```
