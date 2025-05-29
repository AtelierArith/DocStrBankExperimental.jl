```
integrate(eq, x; kwargs...)
```

は、変数 `x` に関して一変数の式 `eq` を統合するための主なエントリーポイントです（オプション）。

```julia
julia> using Symbolics, SymbolNumericIntegration

julia> @variables x a

julia> integrate(x * sin(2x))
((1//4)*sin(2x) - (1//2)*x*cos(2x), 0, 0)

julia> integrate(x * sin(a * x), x; symbolic = true, detailed = false)
(sin(a*x) - a*x*cos(a*x)) / (a^2)

julia> integrate(x * sin(a * x), (x, 0, 1); symbolic = true, detailed = false)
(sin(a) - a*cos(a)) / (a^2)
```

## 引数:

  * `eq`: 一変数の式
  * `x`: 独立変数（`eq` が一変数の場合はオプション）または定積分のための（独立変数、下限、上限）のタプル。

## キーワード引数:

  * `abstol` (デフォルト: `1e-6`): 希望する許容誤差
  * `num_steps` (デフォルト: `2`): 試行する異なるステップの数
  * `num_trials` (デフォルト: `10`): 各ステップでの試行回数（基底に変更なし）
  * `show_basis` (デフォルト: `false`): true の場合、基底（候補項のリスト）が印刷される
  * `bypass` (デフォルト: `false`): true の場合、項を個別に統合せず、一度にすべてを考慮する
  * `symbolic` (デフォルト: `false`): 最初に記号的統合を試みる（`eq` に記号定数がある場合は強制される）
  * `max_basis` (デフォルト: `100`): 考慮する候補項の最大数
  * `verbose` (デフォルト: `false`): 詳細なレポートを印刷する
  * `complex_plane` (デフォルト: `true`): 複素平面上にランダムなテストポイントを生成する（false の場合、ポイントは実軸上にある）
  * `radius` (デフォルト: `1.0`): 複素平面上にランダムなテストポイントを生成するための円盤の半径
  * `opt` (デフォルト: `STLSQ(exp.(-10:1:0))`): スパース回帰最適化器（DataDrivenSparse から）
  * `homotopy` (デフォルト: `true`): *非推奨*、将来のバージョンで削除される予定
  * `use_optim` (デフォルト: `false`): *非推奨*、将来のバージョンで削除される予定
  * `detailed` (デフォルト: `true`): `(solved, unsolved, err)` 出力形式。`detailed=false` の場合、最終的な積分のみが返される。

`detailed == true` の場合、(solved, unsolved, err) のタプルを返します。ここで、

```
solved: 解決された積分 
unsolved: 入力の残りの未解決部分
err: 解決に至る数値誤差
```

`detailed == false` の場合、結果の積分または何も返されません。
