```
CSTR(V, states; initial_states = nothing, name)
```

連続撹拌槽反応器 (CSTR)。このシステムは、反応なしでのCSTRの質量流量を定義します。反応は外部システムから供給されます。体積 $V$ と流量 $q$ を持つCSTRにおける成分 $C$ の質量移動は次のように定義されます：     $\frac{dC}{dt} = (C_{in} - C) * \frac{q}{V} + r_C$ ここで、$r_C$ は成分に対応する外部供給反応速度です。

# パラメータ:

  * `V`: CSTRの体積
  * `states`: CSTRが持つべき成分と、その質量移動が定義される成分
  * `initial_states`: CSTR内の初期濃度

# 状態:

  * `states` パラメータで定義された各成分のための1つの状態

# コネクタ:

  * `inflow`: CSTRの流入
  * `outflow`: CSTRの流出
  * `state`: CSTR内のすべての状態の現在の値
  * `rates`: 各状態の反応速度の入力
