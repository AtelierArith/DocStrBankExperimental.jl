```
primal_dual_semismooth_Newton(M, N, cost, p, X, m, n, prox_F, diff_prox_F, prox_G_dual, diff_prox_dual_G, linearized_operator, adjoint_linearized_operator)
```

プライマル-双対リーマン半滑らかニュートンアルゴリズムを実行します。

与えられた `cost` 関数 $\mathcal E: \mathcal M → \overline{ℝ}$ は次の形式です。

$$
\mathcal E(p) = F(p) + G( Λ(p) ),
$$

ここで $F: \mathcal M → \overline{ℝ}$、$G: \mathcal N → \overline{ℝ}$、および $Λ: \mathcal M → \mathcal N$ です。残りの入力パラメータは次のとおりです。

  * `p, X`:                          プライマルおよび双対の開始点 $p∈\mathcal M$ および $X ∈ T_n\mathcal N$
  * `m,n`:                           $\mathcal M$ および ``\mathcal N` の基準点。
  * `linearized_forward_operator`:   演算子 $Λ(⋅)$ の線形化 $DΛ(⋅)[⋅]$。
  * `adjoint_linearized_operator`:   線形化演算子 $DΛ(m):  T_{m}\mathcal M → T_{Λ(m)}\mathcal N$ の随伴 $DΛ^*$。
  * `prox_F, prox_G_Dual`:           $F$ および $G^\ast_n$ の近接写像。
  * `diff_prox_F, diff_prox_dual_G`: $F$ および $G^\ast_n$ の近接写像の (クラーク一般化) 微分。

アルゴリズムの詳細については、[DiepeveenLellmann:2021](@cite) を参照してください。

# キーワード引数

  * `dual_stepsize=1/sqrt(8)`: 双対近接のプロキシマルパラメータ。
  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: 配列を返す関数、例えば点や接ベクトルが、その結果を割り当てることで動作するか（[`AllocatingEvaluation`](@ref)）、または入力引数を修正してその中で結果を返すか（[`InplaceEvaluation`](@ref)）を指定します。通常、最初の引数は多様体であり、修正された引数は2番目の引数です。
  * `inverse_retraction_method=`[`default_inverse_retraction_method`](@extref `ManifoldsBase.default_inverse_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する逆リトラクション $\operatorname{retr}^{-1}$、詳細は [リトラクションとその逆に関するセクション](@extref ManifoldsBase :doc:`retractions`) を参照してください。
  * `Λ=missing`: `Λ(m)=n` が成り立たない場合に必要な正確な演算子；`missing` は前方演算子が正確であることを示します。
  * `primal_stepsize=1/sqrt(8)`: プライマル近接のプロキシマルパラメータ。
  * `reg_param=1e-5`: ニュートン行列の正則化パラメータ。これは `forward_operator` が呼び出される引数を変更します。
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用するリトラクション $\operatorname{retr}$、詳細は [リトラクションに関するセクション](@extref ManifoldsBase :doc:`retractions`) を参照してください。
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(50)`: 停止基準が満たされていることを示すファンクタ。
  * `update_primal_base=missing`: `m` を更新する関数（デフォルトはアイデンティティ/欠落）。
  * `update_dual_base=missing`: `n` を更新する関数（デフォルトはアイデンティティ/欠落）。
  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用するベクトル輸送 $\mathcal T_{⋅←⋅}$、詳細は [ベクトル輸送に関するセクション](@extref ManifoldsBase :doc:`vector_transports`) を参照してください。

その他のすべてのキーワード引数は、状態デコレーター用の [`decorate_state!`](@ref) または目的デコレーター用の [`decorate_objective!`](@ref) に渡されます。

# 出力

得られた近似最小化点 $p^*$。ソルバーの全体的な最終状態を取得するには、特に `return_state=` キーワードについての詳細は [`get_solver_return`](@ref) を参照してください。 ```
