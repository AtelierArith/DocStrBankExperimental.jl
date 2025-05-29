```
proximal_bundle_method(M, f, ∂f, p=rand(M), kwargs...)
proximal_bundle_method!(M, f, ∂f, p, kwargs...)
```

近接バンドル法を実行します $p^{(k+1)} = \operatorname{retr}_{p^{(k)}}(-d_k)$、ここで $\operatorname{retr}$ はリトラクションであり、

$$
d_k = \frac{1}{\mu_k} \sum_{j\in J_k} λ_j^k \mathrm{P}_{p_k←q_j}X_{q_j},
$$

$$
X_{q_j} ∈ ∂f(q_j)
$$

、$p_k$ は最後の真剣な反復、$\mu_k$ は近接パラメータ、$λ_j^k$ はサブソルバーによって提供される二次サブ問題の解であり、例えば [`proximal_bundle_method_subsolver`](@ref) を参照してください。

サブ微分は値集合である可能性がありますが、引数 `∂f` は常にサブ微分から *1* つの要素を返すべきですが、必ずしも決定論的ではありません。

詳細については [HoseiniMonjeziNobakhtianPouryayevali:2021](@cite) を参照してください。

# 入力

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: リーマン多様体 $\mathcal M$
  * `f`: コスト関数 $f: \mathcal M→ ℝ$ を `(M, p) -> v` として実装
  * `∂f`: 使用するサブソルバーを指定する状態。閉形式の解の場合、これは関数のタイプを示します。
  * `p`: 多様体 $\mathcal M$ 上の点

# キーワード引数

  * `α₀=1.2`:          `α` の初期化値、`η` を更新するために使用
  * `bundle_size=50`:  バンドルの最大サイズ
  * `δ=1.0`:           `μ` を更新するためのパラメータ：$δ < 0$ の場合 $μ = \log(i + 1)$、それ以外の場合 $μ += δ μ$
  * `ε=1e-2`:          多様体の単射半径に関連するステップサイズのようなパラメータ
  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: 配列を返す関数、例えば点や接ベクトルが、その結果を割り当てることで動作するか（[`AllocatingEvaluation`](@ref)）または入力引数を修正してその中で結果を返すか（[`InplaceEvaluation`](@ref)）を指定します。通常、最初の引数は多様体であり、修正された引数は2番目のものです。
  * `inverse_retraction_method=`[`default_inverse_retraction_method`](@extref `ManifoldsBase.default_inverse_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する逆リトラクション $\operatorname{retr}^{-1}$、リトラクションとその逆に関するセクションを参照してください [@extref ManifoldsBase :doc:`retractions`]
  * `m=0.0125`:        コスト関数の減少を制御する実数
  * `μ=0.5`:           サブ問題の初期近接パラメータ
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用するリトラクション $\operatorname{retr}$、リトラクションに関するセクションを参照してください [@extref ManifoldsBase :doc:`retractions`]
  * `stopping_criterion=`[`StopWhenLagrangeMultiplierLess`](@ref)`(1e-8)`[`|`](@ref StopWhenAny)[`StopAfterIteration`](@ref)`(5000)`: 停止基準が満たされていることを示すファンクタ
  * `sub_problem=`[`proximal_bundle_method_subsolver`](@ref)`: ソルバー用の問題または閉形式の解関数を指定します。これは割り当て可能またはインプレースです。
  * `sub_state=`[`AllocatingEvaluation`](@ref): 使用するサブソルバーを指定する状態。閉形式の解の場合、これは関数のタイプを示します。
  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用するベクトル輸送 $\mathcal T_{⋅←⋅}$、ベクトル輸送に関するセクションを参照してください [@extref ManifoldsBase :doc:`vector_transports`]

他のすべてのキーワード引数は、状態デコレーター用の [`decorate_state!`](@ref) または目的デコレーター用の [`decorate_objective!`](@ref) に渡されます。

# 出力

得られた近似最小化点 $p^*$。ソルバーの全体的な最終状態を取得するには、特に `return_state=` キーワードについては [`get_solver_return`](@ref) を参照してください。
