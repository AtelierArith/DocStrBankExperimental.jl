```julia
is_rearranged_standard(
    eom::QuestBase.DifferentialEquation
) -> Any
is_rearranged_standard(
    eom::QuestBase.DifferentialEquation,
    degree
) -> Any

```

`eom`内の微分方程式が標準形に配置されているかどうかを確認します。標準形では、各変数の最高導関数が左辺に孤立して現れます。デフォルトの次数は2で、これは2次の微分方程式に対応します。
