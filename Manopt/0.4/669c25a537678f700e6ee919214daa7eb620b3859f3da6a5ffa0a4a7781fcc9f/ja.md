```
ChambollePock(
    M, N, cost, x0, ξ0, m, n, prox_F, prox_G_dual, adjoint_linear_operator;
    forward_operator=missing,
    linearized_forward_operator=missing,
    evaluation=AllocatingEvaluation()
)
```

リーマン的チャンボール—ポックアルゴリズムを実行します。

次の形式の `cost` 関数 $\mathcal E:\mathcal M → ℝ$ が与えられます。

$$
\mathcal E(p) = F(p) + G( Λ(p) ),
$$

ここで、$F:\mathcal M → ℝ$、$G:\mathcal N → ℝ$、および $Λ:\mathcal M → \mathcal N$ です。残りの入力パラメータは次のとおりです。

  * `p, X`:                         プライマルおよびデュアルの開始点 $x∈\mathcal M$ と $ξ∈T_n\mathcal N$
  * `m,n`:                          $\mathcal M$ および $\mathcal N$ の基準点。
  * `adjoint_linearized_operator`:  線形化された演算子 $DΛ(m): T_{m}\mathcal M → T_{Λ(m)}\mathcal N$ の随伴 $DΛ^*$
  * `prox_F, prox_G_Dual`:          $F$ および $G^\ast_n$ の近接写像

[`AbstractEvaluationType`](@ref) `evaluation` に応じて、最後の3つのパラメータと前方演算子 `Λ` および `linearized_forward_operator` は、割り当て関数 `(Manifolds, parameters) -> result` またはミューテーション関数 `(Manifold, result, parameters)` -> result` として与えることができます。

デフォルトでは、これは正確なリーマン的チャンボール・ポックアルゴリズムを実行します。線形化されたバリアントについては、オプションのパラメータ `DΛ` を参照してください。

アルゴリズムの詳細については、[BergmannHerzogSilvaLouzeiroTenbrinckVidalNunez:2021](@cite) を参照してください。

# オプションのパラメータ

  * `acceleration`:                (`0.05`)
  * `dual_stepsize`:               (`1/sqrt(8)`) プライマル近接の近接パラメータ
  * `evaluation`:                  ([`AllocatingEvaluation`](@ref)`()) 近接写像と演算子が割り当て関数`(Manifolds, parameters) -> result`またはミューテーション関数`(Manifold, result, parameters)`-> result`であるかを指定
  * `Λ`:                           (`missing`) 演算子 $Λ(⋅)$ （`:exact` バリアントに必要）
  * `linearized_forward_operator`: (`missing`) その線形化 $DΛ(⋅)[⋅]$ （`:linearized` バリアントに必要）
  * `primal_stepsize`:             (`1/sqrt(8)`) デュアル近接の近接パラメータ
  * `relaxation`:                  (`1.`) リラクゼーションパラメータ $γ$
  * `relax`:                       (`:primal`) プライマルまたはデュアルをリラックスするか
  * `variant`:                     (`:exact` if `Λ` is missing, otherwise `:linearized`) 使用するバリアント。これにより、`forward_operator` が呼び出される引数が変更されます。
  * `stopping_criterion`:          (`[StopAfterIteration`](@ref)`(100)`) [`StoppingCriterion`](@ref)
  * `update_primal_base`:          (`missing`) `m` を更新する関数（デフォルトはアイデンティティ/欠落）
  * `update_dual_base`:            (`missing`) `n` を更新する関数（デフォルトはアイデンティティ/欠落）
  * `retraction_method`:           (`default_retraction_method(M, typeof(p))`) 使用する再収束
  * `inverse_retraction_method`    (`default_inverse_retraction_method(M, typeof(p))`) 使用する逆再収束。
  * `vector_transport_method`      (`default_vector_transport_method(M, typeof(p))`) 使用するベクトル輸送

# 出力

得られた（近似的な）最小化点 $p^*$、詳細については [`get_solver_return`](@ref) を参照してください。
