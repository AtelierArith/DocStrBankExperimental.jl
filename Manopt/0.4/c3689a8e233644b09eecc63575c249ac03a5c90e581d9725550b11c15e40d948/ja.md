```
proximal_bundle_method(M, f, ∂f, p)
```

近接バンドル法を実行します $p_{j+1} = \mathrm{retr}(p_k, -d_k)$、ここで

$$
d_k = \frac{1}{\mu_l} \sum_{j\in J_k} λ_j^k \mathrm{P}_{p_k←q_j}X_{q_j},
$$

ここで $X_{q_j}\in∂f(q_j)$、$\mathrm{retr}$ はリトラクション、$p_k$ は最後の真剣な反復、$\mu_l$ は近接パラメータ、$λ_j^k$ は [`proximal_bundle_method_subsolver`](@ref) によって提供される二次サブ問題の解です。

サブ微分は集合値である可能性がありますが、引数 `∂f` は常にサブ微分から *1* つの要素を返すべきですが、必ずしも決定論的ではありません。

詳細については [HoseiniMonjeziNobakhtianPouryayevali:2021](@cite) を参照してください。

# 入力

  * `M`: 多様体 $\mathcal M$
  * `f`: 最小化するコスト関数 $F:\mathcal M → ℝ$
  * `∂f`: サブ微分 $∂ f: \mathcal M → T\mathcal M$ で、常にサブ微分から1つの値/要素のみを返すように制限されています。この関数は、割り当て関数 `(M, p) -> X` または変異関数 `(M, X, p) -> X` として渡すことができ、`evaluation` を参照してください。
  * `p`: 初期値 $p ∈ \mathcal M$

# オプション

  * `m`: コスト関数の減少を制御する実数
  * `evaluation`: ([`AllocatingEvaluation`](@ref)) サブグラデーションが割り当て（デフォルト）形式 `∂f(M, q)` で動作するか、[`InplaceEvaluation`](@ref) でインプレース、すなわち `∂f!(M, X, p)` の形式であるかを指定します。
  * `inverse_retraction_method`: (`default_inverse_retraction_method(M, typeof(p))`) 使用する逆リトラクション法
  * `retraction`: (`default_retraction_method(M, typeof(p))`) 使用する `retraction(M, p, X)`。
  * `stopping_criterion`: ([`StopWhenLagrangeMultiplierLess`](@ref)`(1e-8)`) 停止条件を示すファンクタ、[`StoppingCriterion`](@ref) を参照してください。
  * `vector_transport_method`: (`default_vector_transport_method(M, typeof(p))`) 使用するベクトル輸送法

および [`decorate_state!`](@ref) に渡されるデコレーター用のもの。

# 出力

得られた（近似的な）最小化点 $p^*$、詳細については [`get_solver_return`](@ref) を参照してください。
