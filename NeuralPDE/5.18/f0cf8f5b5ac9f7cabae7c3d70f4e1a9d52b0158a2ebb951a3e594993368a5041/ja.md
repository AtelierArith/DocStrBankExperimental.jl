```
QuadratureTraining(; quadrature_alg = CubatureJLh(), reltol = 1e-6, abstol = 1e-3,
                    maxiters = 1_000, batch = 100)
```

損失関数を領域上の ||condition|| の積分として扱うトレーニング戦略です。選択した許容誤差に対してこの損失の（適応的）数値積分を計算するために、Integrals.jl アルゴリズムを使用し、与えられた積分関数呼び出しで評価する最大ポイント数に対応するバッチ `batch` を使用します。

## キーワード引数

  * `quadrature_alg`: 数値積分アルゴリズム,
  * `reltol`: 相対誤差,
  * `abstol`: 絶対誤差,
  * `maxiters`: 数値積分アルゴリズムの最大反復回数,
  * `batch`: バッチするポイントの推奨数.

引数の値やアルゴリズムの選択についての詳細は、[Integrals.jl](https://docs.sciml.ai/Integrals/stable/)を参照してください。
