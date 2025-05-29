```
T_ciic, v_ciic = ciic_temperature(model, p; T0 = nothing, v0 = nothing)
```

与圧力に対する熱力学モデルの特性等圧変曲点（CIIC）を計算します。

CIICは、等温線に沿った最大等圧熱容量（Cp）の点を表し、等圧線に沿ったCpの最大値を表すウィドム線とは対照的です。

# 引数

  * `model`: 計算に使用される熱力学モデル
  * `p`: CIIC温度を計算する圧力
  * `T0`: オプションの初期温度推定値。提供されない場合はデフォルト値が使用されます
  * `v0`: オプションの初期体積推定値。提供されない場合はデフォルト値が使用されます

# 戻り値

  * `T_ciic`: 指定された圧力に対するCIIC点の温度
  * `v_ciic`: CIIC点の体積

# 例

```julia
model = PCSAFT(["methane"])
p = 150e5  # 150 bar
T_ciic, v_ciic = ciic_temperature(model, p)
```
