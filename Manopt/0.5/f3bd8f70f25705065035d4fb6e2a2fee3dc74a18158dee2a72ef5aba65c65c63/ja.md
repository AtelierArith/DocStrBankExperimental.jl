```
PrimalDualManifoldObjective{T<:AbstractEvaluationType} <: AbstractPrimalDualManifoldObjective{T}
```

目的は、線形化されたまたは正確なChambolle-Pockアルゴリズムを記述します。参照：[BergmannHerzogSilvaLouzeiroTenbrinckVidalNunez:2021](@cite)、[ChambollePock:2011](@cite)

# フィールド

`!!`が付いたすべてのフィールドは、コンストラクタの`evaluation=`キーワードに応じて設定され、`T <: AbstractEvaluationType`に格納されるインプレースまたはアロケーション関数である可能性があります。

  * `cost`:                          中間コスト関数値を評価するための$F + G(Λ(⋅))$
  * `linearized_forward_operator!!`: アルゴリズム内の前方操作のための線形化された演算子$DΛ$
  * `linearized_adjoint_operator!!`: 隣接微分$(DΛ)^* : \mathcal N → T\mathcal M$
  * `prox_f!!`:                      $f$に属する近接写像
  * `prox_G_dual!!`:                 $g_n^*$に属する近接写像
  * `Λ!!`:                           前方演算子（与えられた場合）$Λ: \mathcal M → \mathcal N$

通常、線形化された演算子$DΛ$または$Λ$のいずれかが必要です。

# コンストラクタ

```
PrimalDualManifoldObjective(cost, prox_f, prox_G_dual, adjoint_linearized_operator;
    linearized_forward_operator::Union{Function,Missing}=missing,
    Λ::Union{Function,Missing}=missing,
    evaluation::AbstractEvaluationType=AllocatingEvaluation()
)
```

最後のオプション引数は、4または5の関数をアロケーションまたはミューテーション（インプレース計算）として提供するために使用できます。最初の引数は常に考慮される多様体であり、変更されたものは2番目の引数です。
