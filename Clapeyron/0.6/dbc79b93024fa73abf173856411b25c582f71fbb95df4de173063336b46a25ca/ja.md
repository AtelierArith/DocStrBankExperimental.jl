```
p_ciic, v_ciic = ciic_pressure(model, T; p0 = nothing, v0 = nothing)
```

与えられた温度で熱力学モデルの特性等圧変曲点（CIIC）を計算します。

CIICは、等温線に沿った最大等圧比熱容量（Cp）の点を表し、等圧線に沿ったCpの最大値を表すウィドム線とは対照的です。

# 引数

  * `model`: 計算に使用される熱力学モデル
  * `T`: CIIC圧力を計算する温度
  * `p0`: オプションの初期圧力推定値。提供されない場合はデフォルト値が使用されます
  * `v0`: オプションの初期体積推定値。提供されない場合はデフォルト値が使用されます

# 戻り値

  * `p_ciic`: 指定された温度でのCIIC点の圧力
  * `v_ciic`: CIIC点での体積

# 例

```julia
model = PCSAFT(["methane"])
T = 200.0  # 200 K
p_ciic, v_ciic = ciic_pressure(model, T)
```
