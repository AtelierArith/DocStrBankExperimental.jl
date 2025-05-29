```
RegularizedFrankWolfe <: AbstractRegularized
```

フランク・ウォルフアルゴリズムに依存して確率分布を定義しながら解決する正則化最適化レイヤー

```
ŷ(θ) = argmax_{y ∈ C} {θᵀy - Ω(y)}
```

!!! warning
    これは条件付き依存関係であるため、`RegularizedFrankWolfe`を使用する前に以下のパッケージをロードしておく必要があります：

      * `DifferentiableFrankWolfe.jl`
      * `FrankWolfe.jl`
      * `ImplicitDifferentiation.jl`


# フィールド

  * `linear_maximizer`: 線形最大化オラクル `θ -> argmax_{x ∈ C} θᵀx`、ポリトープ `C` を暗黙的に定義
  * `Ω`: 正則化関数 `Ω(y)`
  * `Ω_grad`: 正則化関数の勾配関数 `∇Ω(y)`
  * `frank_wolfe_kwargs`: フランク・ウォルフアルゴリズムに渡されるキーワード引数の名前付きタプル
  * `implicit_kwargs`: 暗黙的微分アルゴリズムに渡されるキーワード引数の名前付きタプル（特に、必要な線形ソルバー）

# フランク・ウォルフパラメータ

調整可能な値：

  * `epsilon::Float64`: 精度目標
  * `max_iteration::Integer`: 最大反復回数
  * `timeout::Float64`: 最大実行時間（秒）
  * `lazy::Bool`: キャッシング戦略
  * `away_steps::Bool`: ジグザグを避ける
  * `line_search::FrankWolfe.LineSearchMethod`: ステップサイズの選択
  * `verbose::Bool`: コンソール出力

詳細についてはFrankWolfe.jlのドキュメントを参照してください。
