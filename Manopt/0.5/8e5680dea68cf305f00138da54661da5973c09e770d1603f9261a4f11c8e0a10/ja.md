```
conjugate_gradient_descent(M, f, grad_f, p=rand(M))
conjugate_gradient_descent!(M, f, grad_f, p)
conjugate_gradient_descent(M, gradient_objective, p)
conjugate_gradient_descent!(M, gradient_objective, p; kwargs...)
```

共役勾配に基づく降下を実行します-

$$
p_{k+1} = \operatorname{retr}_{p_k} \bigl( s_kδ_k \bigr),
$$

ここで、$\operatorname{retr}$は`Manifold` `M`上のリトラクションを示し、降下方向$δ_k$を更新するために、前の方向$δ_{k-1}$と両方の勾配$\operatorname{grad}f(x_k)$、$\operatorname{grad} f(x_{k-1})$に基づいて異なるルールを使用できます。 [`Stepsize`](@ref) $s_k$は[`Linesearch`](@ref)によって決定される場合があります。

`f`と`grad_f`の代わりに、[`AbstractManifoldGradientObjective`](@ref) `gradient_objective`を直接提供することもできます。

利用可能な更新ルールは、[`SteepestDescentCoefficientRule`](@ref)で、これは[`gradient_descent`](@ref)を生成し、[`ConjugateDescentCoefficient`](@ref)（デフォルト）、[`DaiYuanCoefficientRule`](@ref)、[`FletcherReevesCoefficient`](@ref)、[`HagerZhangCoefficient`](@ref)、[`HestenesStiefelCoefficient`](@ref)、[`LiuStoreyCoefficient`](@ref)、および[`PolakRibiereCoefficient`](@ref)です。これらはすべて[`ConjugateGradientBealeRestartRule`](@ref)ルールと組み合わせることができます。

これらはすべて$β_k$を計算し、このアルゴリズムが探索方向を次のように更新します。

$$
δ_k=\operatorname{grad}f(p_k) + β_k \delta_{k-1}
$$

# 入力

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: リーマン多様体$\mathcal M$
  * `f`: コスト関数$f: \mathcal M→ ℝ$を実装したもの`(M, p) -> v`
  * `grad_f`: fの（リーマン）勾配$\operatorname{grad}f: \mathcal M → T_{p}\mathcal M$を関数`(M, p) -> X`または関数`(M, X, p) -> X`として計算し、`X`をインプレースで計算します
  * `p`: 多様体$\mathcal M$上の点

# キーワード引数

  * `coefficient::DirectionUpdateRule=`[`ConjugateDescentCoefficient`](@ref)`()`: 降下方向更新係数$β_k$を計算するルールで、ファンクタとして、結果の関数マップは`(amp, cgs, k) -> β`であり、`amp`は[`AbstractManoptProblem`](@ref)、`cgs`は[`ConjugateGradientDescentState`](@ref)、`k`は現在の反復です。
  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: 配列を返す関数、例えば点や接ベクトルが、その結果を割り当てることによって動作するか（[`AllocatingEvaluation`](@ref)）、または入力引数を修正してその中で結果を返すか（[`InplaceEvaluation`](@ref)）を指定します。通常、最初の引数は多様体であるため、修正された引数は2番目になります。
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用するリトラクション$\operatorname{retr}$、リトラクションに関するセクションを参照してください（@extref ManifoldsBase :doc:`retractions`）
  * `stepsize=`[`ArmijoLinesearch`](@ref)`()`: ステップサイズを決定するための[`Stepsize`](@ref)から継承されたファンクタ
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(500)`[`|`](@ref StopWhenAny)[`StopWhenGradientNormLess`](@ref)`(1e-8)`: 停止基準が満たされていることを示すファンクタ
  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用するベクトル輸送$\mathcal T_{⋅←⋅}$、ベクトル輸送に関するセクションを参照してください（@extref ManifoldsBase :doc:`vector_transports`）

[`ManifoldGradientObjective`](@ref)を直接提供する場合、`evaluation=`キーワードは無視されます。装飾は目的に対して引き続き適用されます。

# 出力

得られた近似最小化点$p^*$。ソルバーの最終状態全体を取得するには、[`get_solver_return`](@ref)を参照してください。特に`return_state=`キーワードに注意してください。 ```
