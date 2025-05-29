```julia
first_order_transform!(
    diff_eom::QuestBase.DifferentialEquation,
    time
)

```

高次の微分方程式系を追加の変数を導入することによって同等の一次系に変換します。システムをその場で修正します。`time`パラメータは、微分に使用される独立変数を指定します。
