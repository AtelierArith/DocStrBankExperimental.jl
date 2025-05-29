```
DouglasRachfordState <: AbstractManoptSolverState
```

ダグラス・ラチフォードアルゴリズムに必要なすべてのオプションを格納します。

# フィールド

  * `α`:                         古い反復から新しい反復へのステップの緩和、正確には $x^{(k+1)} = g(α(k); x^{(k)}, t^{(k)})$、ここで $t^{(k)}$ はDRアルゴリズムに関与する二重反射の結果です
  * `inverse_retraction_method::AbstractInverseRetractionMethod`: 使用する逆引き戻し $\operatorname{retr}^{-1}$、詳細は[引き戻しとその逆に関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照してください
  * `λ`:                         呼び出し中の近接パラメータの値を提供する関数
  * `parallel`:                  並列ダグラス・ラチフォードを使用するかどうかを示します。
  * `R`:                          近接点 `p` での `x` の反射を実行するために反復で使用されるメソッド。
  * `p::P`: マニフォールド $\mathcal M$ 上の点で、現在の反復を格納します。並列ダグラス・ラチフォードの場合、これは `PowerManifold` マニフォールドからの値ではなく、平均です。
  * `reflection_evaluation`:     `R` がインプレースで動作するか、割り当てを行うか
  * `retraction_method::AbstractRetractionMethod`: 使用する引き戻し $\operatorname{retr}$、詳細は[引き戻しに関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照してください
  * `s`:                         近接マップでの二重反射の最後の結果を `α` で緩和したもの。
  * `stop::StoppingCriterion`: 停止基準が満たされていることを示すファンクタ

# コンストラクタ

```
DouglasRachfordState(M::AbstractManifold; kwargs...)
```

# 入力

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: リーマン多様体 $\mathcal M$

# キーワード引数

  * `α= k -> 0.9`: 古い反復から新しい反復へのステップの緩和、正確には $x^{(k+1)} = g(α(k); x^{(k)}, t^{(k)})$、ここで $t^{(k)}$ はDRアルゴリズムに関与する二重反射の結果です
  * `inverse_retraction_method=`[`default_inverse_retraction_method`](@extref `ManifoldsBase.default_inverse_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する逆引き戻し $\operatorname{retr}^{-1}$、詳細は[引き戻しとその逆に関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照してください
  * `λ= k -> 1.0`: 呼び出し中の近接パラメータの値を提供する関数
  * `p=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`: 初期値を指定するためのマニフォールド $\mathcal M$ 上の点
  * `R=`[`reflect`](@ref)`(!)`: 近接点 `p` の反射を実行するために反復で使用されるメソッド、どの関数が使用されるかは `reflection_evaluation` に依存します。
  * `reflection_evaluation=`[`AllocatingEvaluation`](@ref)`()`) 反射がインプレースで動作するか、割り当てを行うかを指定します（デフォルト）
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する引き戻し $\operatorname{retr}$、詳細は[引き戻しに関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照してください
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(300)`: 停止基準が満たされていることを示すファンクタ
  * `parallel=false`: 並列ダグラス・ラチフォードを使用するかどうかを示します。
