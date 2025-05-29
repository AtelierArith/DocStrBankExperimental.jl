```
ChambollePock(M, N, f, p, X, m, n, prox_G, prox_G_dual, adjoint_linear_operator; kwargs...)
ChambollePock!(M, N, f, p, X, m, n, prox_G, prox_G_dual, adjoint_linear_operator; kwargs...)
```

リーマン・シャンボル＝ポックアルゴリズムを実行します。

与えられた `cost` 関数 $\mathcal E:\mathcal M → ℝ$ は次の形式です。

$$
\mathcal f(p) = F(p) + G( Λ(p) ),
$$

ここで、$F:\mathcal M → ℝ$、$G:\mathcal N → ℝ$、および $Λ:\mathcal M → \mathcal N$ です。

これは $p$ のインプレースで行うことができます。

# 入力パラメータ

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: リーマン多様体 $\mathcal M$
  * `N::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: リーマン多様体 $\mathcal M$
  * `p`: 多様体 $\mathcal M$ 上の点
  * `X`: 多様体 $\mathcal M$ 上の点 $p$ における接ベクトル
  * `m`: 多様体 $\mathcal M$ 上の点
  * `n`: 多様体 $\mathcal N$ 上の点
  * `adjoint_linearized_operator`: 線形化された演算子 $DΛ: T_{m}\mathcal M → T_{Λ(m)}\mathcal N)$ の随伴 $DΛ^*$
  * `prox_F, prox_G_Dual`: $F$ と $G^\ast_n$ の近接写像

[`AbstractEvaluationType`](@ref) `evaluation` に応じて、最後の3つのパラメータと前方演算子 `Λ` および `linearized_forward_operator` は、割り当て関数 `(Manifolds, parameters) -> result` または変異関数 `(Manifold, result, parameters)` -> result` として与えることができ、割り当てを節約します。

デフォルトでは、これは正確なリーマン・シャンボル・ポックアルゴリズムを実行します。線形化されたバリアントについてはオプションのパラメータ `DΛ` を参照してください。

アルゴリズムの詳細については、[BergmannHerzogSilvaLouzeiroTenbrinckVidalNunez:2021](@cite) を参照してください。

# キーワード引数

  * `acceleration=0.05`: 加速パラメータ
  * `dual_stepsize=1/sqrt(8)`: プライマル近接の近接パラメータ
  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: 配列を返す関数、例えば点や接ベクトルが結果を割り当てるか、入力引数を修正してその中で結果を返すかを指定します（[`AllocatingEvaluation`](@ref) または [`InplaceEvaluation`](@ref)）。通常、最初の引数は多様体であるため、修正された引数は2番目になります。
  * `inverse_retraction_method=`[`default_inverse_retraction_method`](@extref `ManifoldsBase.default_inverse_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する逆引き戻し $\operatorname{retr}^{-1}$、詳細は [引き戻しとその逆に関するセクション](@extref ManifoldsBase :doc:`retractions`) を参照してください。
  * `inverse_retraction_method_dual=`[`default_inverse_retraction_method`](@extref `ManifoldsBase.default_inverse_retraction_method-Tuple{AbstractManifold}`)`(N, typeof(n))`: 使用する逆引き戻し $\operatorname{retr}^{-1}$、詳細は [引き戻しとその逆に関するセクション](@extref ManifoldsBase :doc:`retractions`) を参照してください。
  * `Λ=missing`: （前方）演算子 $Λ(⋅)$ （`:exact` バリアントに必要）
  * `linearized_forward_operator=missing`: その線形化 $DΛ(⋅)[⋅]$ （`:linearized` バリアントに必要）
  * `primal_stepsize=1/sqrt(8)`: デュアル近接の近接パラメータ
  * `relaxation=1.`: リラクゼーションパラメータ $γ$
  * `relax=:primal`: プライマルまたはデュアルをリラックスするか
  * `variant=:exact` `Λ` が欠けている場合、そうでなければ `:linearized`: 使用するバリアント。これは `forward_operator` が呼び出される引数を変更します。
  * `stopping_criterion=`[StopAfterIteration`](@ref)`(100)`: 停止基準が満たされていることを示すファンクタ
  * `update_primal_base=missing`: `m` を更新する関数（デフォルト/欠落は恒等関数）
  * `update_dual_base=missing`: `n` を更新する関数（デフォルト/欠落は恒等関数）
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する引き戻し $\operatorname{retr}$、詳細は [引き戻しに関するセクション](@extref ManifoldsBase :doc:`retractions`) を参照してください。
  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用するベクトル輸送 $\mathcal T_{⋅←⋅}$、詳細は [ベクトル輸送に関するセクション](@extref ManifoldsBase :doc:`vector_transports`) を参照してください。
  * `vector_transport_method_dual=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(N, typeof(n))`: 使用するベクトル輸送 $\mathcal T_{⋅←⋅}$、詳細は [ベクトル輸送に関するセクション](@extref ManifoldsBase :doc:`vector_transports`) を参照してください。

# 出力

得られた近似最小化点 $p^*$。ソルバーの全体的な最終状態を取得するには、[`get_solver_return`](@ref) を参照してください。特に `return_state=` キーワードに注意してください。 ```
