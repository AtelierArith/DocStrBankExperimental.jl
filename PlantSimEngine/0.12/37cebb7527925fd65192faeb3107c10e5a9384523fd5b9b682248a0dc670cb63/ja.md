```
NRMSE(obs,sim)
```

観測値 `obs` とシミュレーション `sim` の間の正規化された二乗平均平方根誤差を返します。正規化は観測値の範囲（最大値-最小値）での割り算を使用して行われます。

# 例

```@example
using PlantSimEngine

obs = [1.0, 2.0, 3.0]
sim = [1.1, 2.1, 3.1]

NRMSE(obs, sim)
```
