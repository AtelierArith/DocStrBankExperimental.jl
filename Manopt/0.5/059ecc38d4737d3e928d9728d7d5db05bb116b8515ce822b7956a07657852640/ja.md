```
projected_gradient_method(M, f, grad_f, proj, p=rand(M); kwargs...)
projected_gradient_method(M, obj::ManifoldConstrainedSetObjective, p=rand(M); kwargs...)
projected_gradient_method!(M, f, grad_f, proj, p; kwargs...)
projected_gradient_method!(M, obj::ManifoldConstrainedSetObjective, p; kwargs...)
```

制約付き問題に対する投影勾配法を計算します

$$
\begin{aligned}
\operatorname*{arg\,min}_{p ∈ \mathcal M} & f(p)\\
\text{subject to}\quad& p ∈ \mathcal C ⊂ \mathcal M
\end{aligned}
$$

次のステップを実行することによって

1. `stepsize` $α_k$ を使用して候補 $q_k = \operatorname{proj}_{\mathcal C}\Bigl(\operatorname{retr}_{p_k}\bigl(-α_k \operatorname{grad} f(p_k)\bigr)\Bigr)$ を計算します
2. $$
    Y_k = \operatorname{retr}_{p_k}^{-1}q_k
    $$

    に沿ったバックトラッキングステップサイズ $β_k ≤ 1$ を計算します
3. 新しい反復 $p_{k+1} = \operatorname{retr}_{p_k}( β_k \operatorname{retr}_{p_k}^{-1}q_k )$ を計算します

`stopping_criterion=` が満たされるまで。

詳細については [BergmannFerreiraNemethZhu:2025](@cite) を参照してください。

# 入力

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: リーマン多様体 $\mathcal M$
  * `f`: コスト関数 $f: \mathcal M→ ℝ$ を `(M, p) -> v` として実装
  * `grad_f`: f の (リーマン) 勾配 $\operatorname{grad}f: \mathcal M → T_{p}\mathcal M$ を `(M, p) -> X` または `(M, X, p) -> X` として計算する関数
  * `proj` 集合 $\mathcal C$ への射影を行う関数 `(M, p) -> q` または `(M, q, p) -> q` として `q` の射影をインプレースで計算する関数
  * `p`: 多様体 $\mathcal M$ 上の点

# キーワード引数

  * `backtrack=`[`ArmijoLinesearchStepsize`](@ref)`(M; stop_increasing_at_step=0)`: バックトラッキングを行うためのステップサイズを決定する [`Stepsize`](@ref) から継承されたファンクタ。$β_k ≤ 1$ が必要であることに注意してください。そうでない場合、射影ステップは制約内の点を提供しなくなります
  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: 配列を返す関数、例えば点や接ベクトルがその結果を割り当てて動作するか（[`AllocatingEvaluation`](@ref)）、または入力引数を修正してその中で結果を返すか（[`InplaceEvaluation`](@ref)）を指定します。通常、最初の引数は多様体であり、修正された引数は2番目のものです。
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する引き戻し $\operatorname{retr}$、詳細は [引き戻しに関するセクション](@extref ManifoldsBase :doc:`retractions`) を参照
  * `stepsize=`[`ConstantStepsize`](@ref)`(injectivity_radius(M)/2)`: 候補の投影ステップを実行するためのステップサイズを決定する [`Stepsize`](@ref) から継承されたファンクタ
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(500)`[`|`](@ref StopWhenAny)``[`StopWhenGradientNormLess`](@ref)`(1.0e-6)`: 停止基準が満たされることを示すファンクタ

他のすべてのキーワード引数は、状態デコレーター用の [`decorate_state!`](@ref) または目的デコレーター用の [`decorate_objective!`](@ref) に渡されます。

# 出力

得られた近似最小化点 $p^*$。ソルバーの全体的な最終状態を取得するには、特に `return_state=` キーワードについての詳細は [`get_solver_return`](@ref) を参照してください。
