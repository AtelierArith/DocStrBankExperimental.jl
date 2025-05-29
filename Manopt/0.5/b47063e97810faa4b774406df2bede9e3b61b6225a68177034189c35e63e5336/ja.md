```
PrimalDualManifoldSemismoothNewtonObjective{E<:AbstractEvaluationType, TC, LO, ALO, PF, DPF, PG, DPG, L} <: AbstractPrimalDualManifoldObjective{E, TC, PF}
```

プライマル-デュアルリーマン半滑らかニュートンアルゴリズムの問題を説明します。 [DiepeveenLellmann:2021](@cite)

# フィールド

  * `cost`:                        $F + G(Λ(⋅))$ 中間コスト関数値を評価するため
  * `linearized_operator`:         演算子 $Λ(⋅)$ の線形化 $DΛ(⋅)[⋅]$。
  * `linearized_adjoint_operator`: 隣接微分 $(DΛ)^* : \mathcal N → T\mathcal M$
  * `prox_F`:                      $F$ に属する近接写像
  * `diff_prox_F`:                 $F$ の近接写像の (クラーク一般化) 微分
  * `prox_G_dual`:                 `G^\ast_n`` に属する近接写像
  * `diff_prox_dual_G`:            $G^\ast_n$ の近接写像の (クラーク一般化) 微分
  * `Λ`:                           正確な前方演算子。この演算子は `Λ(m)=n` が成り立たない場合に必要です。

# コンストラクタ

```
PrimalDualManifoldSemismoothNewtonObjective(cost, prox_F, prox_G_dual, forward_operator, adjoint_linearized_operator,Λ)
```
