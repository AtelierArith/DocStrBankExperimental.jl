```julia
rearrange_standard!(eom::QuestBase.DifferentialEquation)
rearrange_standard!(
    eom::QuestBase.DifferentialEquation,
    degree
)

```

`eom`内の微分方程式を標準形に再配置します。ここで、各変数の最高次導関数（`degree`で指定、デフォルトは2）が左辺に孤立して現れます。方程式はその場で修正されます。
