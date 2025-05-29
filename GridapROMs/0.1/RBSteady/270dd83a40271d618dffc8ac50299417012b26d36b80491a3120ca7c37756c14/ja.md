```
struct SupremizerReduction{A,R<:Reduction{A,EnergyNorm}} <: Reduction{A,EnergyNorm}
  reduction::R
  supr_op::Function
  supr_tol::Float64
end
```

安定化の追加ステップを必要とする削減手法 `reduction` のラッパーで、スプレミナイザーの強化によって実現されます。定常状態における詳細については[こちら](https://doi.org/10.1002/nme.4772)を、過渡状態における詳細については[こちら](https://doi.org/10.1137/22M1509114)を確認してください。フィールド `supr_op` と `supr_tol`（これは過渡アプリケーションでのみ必要）は、それぞれスプレミナイザー演算子と強化に関与する許容誤差です。ヤコビ行列が次の形の鞍点問題に対して、

[ A   Bᵀ   B   0 ]

この演算子は行列 Bᵀ を表す双線形形式によって与えられます。
