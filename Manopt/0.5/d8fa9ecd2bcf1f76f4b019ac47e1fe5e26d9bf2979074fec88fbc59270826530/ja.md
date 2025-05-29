```
gradient_descent(M, f, grad_f, p=rand(M); kwargs...)
gradient_descent(M, gradient_objective, p=rand(M); kwargs...)
gradient_descent!(M, f, grad_f, p; kwargs...)
gradient_descent!(M, gradient_objective, p; kwargs...)
```

勾配降下法アルゴリズムを実行します

$$
p_{k+1} = \operatorname{retr}_{p_k}\bigl( s_k\operatorname{grad}f(p_k) \bigr),
\qquad k=0,1,…
$$

ここで、$s_k > 0$ はステップサイズを示します。

アルゴリズムは `p` のインプレースで実行できます。

# 入力

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: リーマン多様体 $\mathcal M$
  * `f`: コスト関数 $f: \mathcal M→ ℝ$ を `(M, p) -> v` として実装
  * `grad_f`: 関数 `(M, p) -> X` または `(M, X, p) -> X` として、$f$ の (リーマン) 勾配 $\operatorname{grad}f: \mathcal M → T_{p}\mathcal M$ を計算する関数
  * `p`: 多様体 $\mathcal M$ 上の点

`f` と `grad_f` の代わりに、対応する [`AbstractManifoldGradientObjective`](@ref) `gradient_objective` を直接提供することもできます。

# キーワード引数

  * `direction=`[`IdentityUpdateRule`](@ref)`()`: 方向の特定の処理を実行するように指定します。例えば [`Nesterov`](@ref)、[`MomentumGradient`](@ref) または [`AverageGradient`](@ref) など。
  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: 配列を返す関数、例えば点や接ベクトルが、結果を割り当てる方法で動作するか（[`AllocatingEvaluation`](@ref)）、入力引数を修正してその中で結果を返すか（[`InplaceEvaluation`](@ref)）を指定します。通常、最初の引数は多様体であり、修正された引数は2番目の引数です。例えば `grad_f(M,p)` は割り当てますが、`grad_f!(M, X, p)` は `X` のインプレースで結果を計算します。
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用するリトラクション $\operatorname{retr}$、リトラクションに関するセクションを参照してください [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `stepsize=`[`default_stepsize`](@ref)`(M, GradientDescentState)`: ステップサイズを決定するための [`Stepsize`](@ref) から継承されたファンクタ
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(200)`[`|`](@ref StopWhenAny)[`StopWhenGradientNormLess`](@ref)`(1e-8)`: 停止基準が満たされていることを示すファンクタ
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`: 現在の反復での勾配を格納する多様体 $\mathcal M$ 上の点 $p$ における接ベクトル

他のすべてのキーワード引数は、状態デコレーター用の [`decorate_state!`](@ref) または目的デコレーター用の [`decorate_objective!`](@ref) に渡されます。

[`ManifoldGradientObjective`](@ref) を直接提供する場合、`evaluation=` キーワードは無視されます。デコレーションは目的に適用されます。

チュートリアルモードを有効にすると（cf. [`is_tutorial_mode`](@ref)）、このソルバーは追加のデバッグ警告を提供します。

# 出力

得られた近似最小化点 $p^*$。ソルバーの最終状態全体を取得するには、詳細については [`get_solver_return`](@ref) を参照してください。特に `return_state=` キーワードを参照してください。
