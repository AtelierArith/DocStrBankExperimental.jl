```
RMSE(obs,sim)
```

観測値 `obs` とシミュレーション `sim` の間の二乗平均平方根誤差を返します。

0に近いほど良いです。

# 例

```@example
using PlantSimEngine

obs = [1.0, 2.0, 3.0]
sim = [1.1, 2.1, 3.1]

RMSE(obs, sim)
```
