```
cma_es(M, f, p_m=rand(M); σ::Real=1.0, kwargs...)
```

共分散行列適応進化戦略探索を実行して、グローバルな勾配フリーのランダム最適化を行います。これは複雑な非凸関数に適しています。`p_m`から3σの距離内でグローバル最小値を見つけることが合理的に期待できます。

実装は[Hansen:2023](@cite)に基づいており、リーマン設定への基本的な適応が行われています。

# 入力

  * `M`:      多様体 $\mathcal M$
  * `f`:      最適化するためのコスト関数 $f: \mathcal M→ℝ$

# キーワード引数

  * `p_m=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`: 初期点 `p`
  * `σ=1.0`: 初期標準偏差
  * `λ`:                  （`4 + Int(floor(3 * log(manifold_dimension(M))))`）集団サイズ（より徹底的なグローバル探索のために増加可能ですが、減少は推奨されません）
  * `tol_fun=1e-12`: `StopWhenPopulationCostConcentrated`の許容誤差、後続の点での関数値の絶対差に類似
  * `tol_x=1e-12`: `StopWhenPopulationStronglyConcentrated`の許容誤差、後続の点間の絶対差に類似ですが、実際には分布パラメータから計算されます。
  * `stopping_criterion=``default_cma_es_stopping_criterion(M, λ; tol_fun=tol_fun, tol_x=tol_x)`: 停止基準が満たされていることを示すファンクタ
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する再traction $\operatorname{retr}$、再tractionに関する[セクション](@extref ManifoldsBase :doc:`retractions`)を参照
  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用するベクトル輸送 $\mathcal T_{⋅←⋅}$、ベクトル輸送に関する[セクション](@extref ManifoldsBase :doc:`vector_transports`)を参照
  * `basis`               (`DefaultOrthonormalBasis()`) 共分散を表現するために使用される基底
  * `rng=default_rng()`: `M`上の新しい点を生成するための乱数生成器

他のすべてのキーワード引数は、状態デコレーター用の[`decorate_state!`](@ref)または目的デコレーター用の[`decorate_objective!`](@ref)にそれぞれ渡されます。

# 出力

得られた近似最小値 $p^*$。ソルバーの最終状態全体を取得するには、特に`return_state=`キーワードについての詳細は[`get_solver_return`](@ref)を参照してください。
