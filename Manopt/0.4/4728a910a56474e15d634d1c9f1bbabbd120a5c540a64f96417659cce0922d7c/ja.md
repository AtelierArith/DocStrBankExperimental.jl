```
primal_dual_semismooth_Newton(M, N, cost, p, X, m, n, prox_F, diff_prox_F, prox_G_dual, diff_prox_dual_G, linearized_operator, adjoint_linearized_operator)
```

プライマル-デュアルリーマン半滑らかニュートンアルゴリズムを実行します。

与えられた `cost` 関数 $\mathcal E: \mathcal M → \overline{ℝ}$ の形式は

$$
\mathcal E(p) = F(p) + G( Λ(p) ),
$$

ここで $F: \mathcal M → \overline{ℝ}$、$G: \mathcal N → \overline{ℝ}$、および $\Lambda: \mathcal M → \mathcal N$ です。残りの入力パラメータは

  * `p, X`:                          プライマルおよびデュアルの開始点 $p∈\mathcal M$ および $X ∈ T_n\mathcal N$
  * `m,n`:                           $\mathcal M$ および $\mathcal N$ の基準点
  * `linearized_forward_operator`:   演算子 $Λ(⋅)$ の線形化 $DΛ(⋅)[⋅]$
  * `adjoint_linearized_operator`:   線形化演算子 $DΛ(m):  T_{m}\mathcal M → T_{Λ(m)}\mathcal N$ の随伴 $DΛ^*$
  * `prox_F, prox_G_Dual`:           $F$ および $G^\ast_n$ の近接写像
  * `diff_prox_F, diff_prox_dual_G`: $F$ および $G^\ast_n$ の近接写像の (クラーク一般化) 微分

アルゴリズムの詳細については、[DiepeveenLellmann:2021](@cite) を参照してください。

# オプションのパラメータ

  * `primal_stepsize`:           （`1/sqrt(8)`）プライマル近接のパラメータ
  * `Λ`:                         （`missing`）`Λ(m)=n` が成り立たない場合に必要な正確な演算子；`missing` は、前方演算子が正確であることを示します。
  * `dual_stepsize`:             （`1/sqrt(8)`）デュアル近接のパラメータ
  * `reg_param`:                 （`1e-5`）ニュートン行列の正則化パラメータ。これは `forward_operator` が呼ばれる引数を変更します。
  * `stopping_criterion`:        （`stopAtIteration(50)`）[`StoppingCriterion`](@ref)
  * `update_primal_base`:        （`missing`）`m` を更新する関数（デフォルトでは恒等関数/欠落）
  * `update_dual_base`:          （`missing`）`n` を更新する関数（デフォルトでは恒等関数/欠落）
  * `retraction_method`:         （`default_retraction_method(M, typeof(p))`）使用する再収束法
  * `inverse_retraction_method`: （`default_inverse_retraction_method(M, typeof(p))`）使用する逆再収束法。
  * `vector_transport_method`:   （`default_vector_transport_method(M, typeof(p))`）使用するベクトル輸送

# 出力

得られた（近似的な）最小化点 $p^*$、詳細については [`get_solver_return`](@ref) を参照してください。
