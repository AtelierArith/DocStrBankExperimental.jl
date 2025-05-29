```
cma_es(M, f, p_m=rand(M); σ::Real=1.0, kwargs...)
```

共分散行列適応進化戦略探索を実行し、グローバルな勾配フリーのランダム最適化を行います。これは複雑な非凸関数に適しています。`p_m`から3σの距離内でグローバル最小値を見つけることが合理的に期待できます。

実装は[Ransen:2023](@cite)に基づいており、リーマン設定への基本的な適応が行われています。

# 入力

  * `M`:      多様体 $\mathcal M$
  * `f`:      最適化するためのコスト関数 $f: \mathcal M→ℝ$

# オプション

  * `p_m`:                （`rand(M)`）初期点 `p`
  * `σ`:                  （`1.0`）初期標準偏差
  * `λ`:                  （`4 + Int(floor(3 * log(manifold_dimension(M))))`）集団サイズ（より徹底的なグローバル探索のために増加させることができますが、減少させることは推奨されません）
  * `tol_fun`:            （`1e-12`）`StopWhenPopulationCostConcentrated`の許容誤差、後続の点での関数値の絶対差に類似
  * `tol_x`:              （`1e-12`）`StopWhenPopulationStronglyConcentrated`の許容誤差、後続の点間の絶対差に類似ですが、実際には分布パラメータから計算されます。
  * `stopping_criterion`: （`default_cma_es_stopping_criterion(M, λ; tol_fun=tol_fun, tol_x=tol_x)`）
  * `retraction_method`:  （`default_retraction_method(M, typeof(p_m))`）
  * `vector_transport_method`: （`default_vector_transport_method(M, typeof(p_m))`）
  * `basis`               （`DefaultOrthonormalBasis()`）共分散を表現するために使用される基底
  * `rng`:                （`default_rng()`）`M`上の新しい点を生成するための乱数生成器

# 出力

得られた（近似的な）最小化点 $p^*$。ソルバーの最終状態全体を取得するには、詳細については[`get_solver_return`](@ref)を参照してください。
