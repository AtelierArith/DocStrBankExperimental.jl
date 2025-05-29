```
piecewisefit(f::Function, domain::Tuple{Real, Real}, formulas::Vector{Formula}; kwargs...)
```

実数値関数 `f(::Real)` のドメイン `domain` における区分近似を返します。配列 `formulas` に与えられた式を使用します（[`Formula`](@ref)を参照）。

## オプションのキーワード引数

  * `parity` : 区分関数にパリティ（`:even` または `:odd`、デフォルトは `:none`）を課す
  * `singularities` : ドメインから除外される点（デフォルトは `[]`）
  * `cuts` : 区分境界として強制される点（デフォルトは `[]`）
  * `grain` : 最小ドメインサイズ、デフォルトは `eps(Float64)`
  * `resolution` : サンプリングされた点の最大距離、デフォルトは `Inf`
  * `rtol` : 相対許容誤差、デフォルトは `0.0`
  * `atol` : 絶対許容誤差、デフォルトは `eps(Float64)`
  * `loop` : ドメイン内で失敗した場合に `f` を返すかどうか、デフォルトは `false`

## 例

ここに関数 $\sin^{-1}(x)$ の1つの区分近似があります。$x=1$ におけるべき法則は正確に表現され、残りには多項式がフィットされています：

```julia-repl
julia> f = PiecewiseFunction(:odd, Piece((0, 1), PLS, [1, 1 / 2, -sqrt(2)])) +
           piecewisefit(x -> asin(x) + sqrt(2 - 2 * x), (0, 1), [POLY],
           parity=:odd, atol=1e-5)
< Piecewise odd function with 1 piece and support [-1.0, 1.0] >

julia> max([abs(f(x) - asin(x)) for x in -1:0.1:1]...) < 1e-5
true
```
