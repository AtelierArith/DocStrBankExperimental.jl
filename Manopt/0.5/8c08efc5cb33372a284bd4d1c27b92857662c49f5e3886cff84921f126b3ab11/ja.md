```
convex_bundle_method(M, f, ∂f, p)
convex_bundle_method!(M, f, ∂f, p)
```

凸バンドル法を実行します $p^{(k+1)} = \operatorname{retr}_{p^{(k)}}(-g_k)$ ここで

$$
g_k = \sum_{j\in J_k} λ_j^k \mathrm{P}_{p_k←q_j}X_{q_j},
$$

とし、$p_k$ は最後の真剣な反復、$X_{q_j} ∈ ∂f(q_j)$ であり、$λ_j^k$ は [`convex_bundle_method_subsolver`](@ref) によって提供される二次サブ問題の解です。

サブ微分は集合値である可能性がありますが、引数 `∂f` は常にサブ微分から1つの要素を返すべきですが、必ずしも決定論的ではありません。

詳細については、[BergmannHerzogJasa:2024](@cite) を参照してください。

# 入力

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: リーマン多様体 $\mathcal M$
  * `f`: コスト関数 $f: \mathcal M→ ℝ$ を `(M, p) -> v` として実装
  * `∂f`: 使用するサブソルバーを指定する状態。閉形式の解の場合、これは関数のタイプを示します。
  * `p`: 多様体 $\mathcal M$ 上の点

# キーワード引数

  * `atol_λ=eps()` : $λ$ における凸係数の許容誤差パラメータ。
  * `atol_errors=eps()`: 線形化誤差の許容誤差パラメータ。
  * `bundle_cap=25``
  * `m=1e-3`: コストの減少をテストするためのパラメータ: $f(q_{k+1}) ≤ f(p_k) + m ξ$。
  * `diameter=50.0`: 開始点における目的関数のレベルセットの直径の推定。
  * `domain=(M, p) -> isfinite(f(M, p))`: 現在の候補が目的 `f` のドメイン内にあるときに真を返し、そうでないときに偽を返す関数。
  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: 配列を返す関数、例えば点や接ベクトルが、その結果を割り当てることで動作するか（[`AllocatingEvaluation`](@ref)）または入力引数を修正してその中で結果を返すか（[`InplaceEvaluation`](@ref)）を指定します。通常、最初の引数は多様体であり、修正された引数は2番目のものです。
  * `k_max=0`: 多様体の断面曲率の上限。
  * `stepsize=`[`default_stepsize`](@ref)`(M, ConvexBundleMethodState)`: ステップサイズを決定するための [`Stepsize`](@ref) から継承されたファンクタ
  * `inverse_retraction_method=`[`default_inverse_retraction_method`](@extref `ManifoldsBase.default_inverse_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する逆引き戻し $\operatorname{retr}^{-1}$、詳細は [引き戻しとその逆に関するセクション](@extref ManifoldsBase :doc:`retractions`) を参照してください。
  * `stopping_criterion=`[`StopWhenLagrangeMultiplierLess`](@ref)`(1e-8)`[`|`](@ref StopWhenAny)[`StopAfterIteration`](@ref)`(5000)`: 停止基準が満たされていることを示すファンクタ
  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用するベクトル輸送 $\mathcal T_{⋅←⋅}$、詳細は [ベクトル輸送に関するセクション](@extref ManifoldsBase :doc:`vector_transports`) を参照してください。
  * `sub_state=`[`convex_bundle_method_subsolver`](@ref)`: 使用するサブソルバーを指定する状態。閉形式の解の場合、これは関数のタイプを示します。
  * `sub_problem=`[`AllocatingEvaluation`](@ref): ソルバーまたは閉形式の解関数のための問題を指定します。これは割り当て可能またはインプレースである可能性があります。
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`: 多様体 $\mathcal M$ 上の点 $p$ における接ベクトル

他のすべてのキーワード引数は、状態デコレーターのために [`decorate_state!`](@ref) に、目的デコレーターのために [`decorate_objective!`](@ref) に渡されます。

# 出力

得られた近似最小化点 $p^*$。ソルバーの全体の最終状態を取得するには、特に `return_state=` キーワードについては [`get_solver_return`](@ref) を参照してください。
