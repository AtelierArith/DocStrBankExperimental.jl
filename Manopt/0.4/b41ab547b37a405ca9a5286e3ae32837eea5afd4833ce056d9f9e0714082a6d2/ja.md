```
DouglasRachfordState <: AbstractManoptSolverState
```

ダグラス・ラチフォードアルゴリズムに必要なすべてのオプションを格納します。

# フィールド

  * `p`:                         現在の反復（結果）並列ダグラス・ラチフォードの場合、これは`PowerManifold`多様体からの値ではなく、平均です。
  * `s`:                         プロキシマルマップでの二重反射の最後の結果、`α`によって緩和されています。
  * `λ`:                         呼び出し中にプロキシマルパラメータの値を提供する関数
  * `α`:                         古い反復から新しい反復へのステップの緩和、正確には $x^{(k+1)} = g(α(k); x^{(k)}, t^{(k)})$、ここで $t^{(k)}$ はDRアルゴリズムに関与する二重反射の結果です。
  * `inverse_retraction_method`: 逆引き戻し法
  * `R`:                          反射を行うために反復で使用されるメソッド `x` をプロキシ `p` で。
  * `reflection_evaluation`:     `R` がインプレースで動作するか、割り当てを行うか
  * `retraction_method`:         引き戻し法
  * `stop`:                      [`StoppingCriterion`](@ref)
  * `parallel`:                  並列ダグラス・ラチフォードを使用するかどうかを示します。

# コンストラクタ

```
DouglasRachfordState(M, p; kwargs...)
```

多様体 `M` と初期点 `p` のオプションを生成します。以下のキーワード引数が使用できます。

  * `λ`:                    （`(iter)->1.0`）呼び出し中にプロキシマルパラメータの値を提供する関数
  * `α`:                    （`(iter)->0.9`）古い反復から新しい反復へのステップの緩和、正確には $x^{(k+1)} = g(α(k); x^{(k)}, t^{(k)})$、ここで $t^{(k)}$ はDRアルゴリズムに関与する二重反射の結果です。
  * `R`:                    （[`reflect`](@ref) または `reflect!`）反復で使用されるメソッド `x` をプロキシ `p` で反射させるために、どの関数が使用されるかは `reflection_evaluation` に依存します。
  * `reflection_evaluation`: （[`AllocatingEvaluation`](@ref)`()`) 反射がインプレースで動作するか、割り当てを行うかを指定します（デフォルト）。
  * `stopping_criterion`:   （[`StopAfterIteration`](@ref)`(300)`) [`StoppingCriterion`](@ref)
  * `parallel`:             （`false`）並列ダグラス・ラチフォードを使用するかどうかを示します。
