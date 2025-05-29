```
EF(obs,sim)
```

観測値 `obs` とシミュレーション `sim` の間の効率係数をNSE（ナッシュ・サットクリフ効率）モデルを使用して返します。詳細情報は https://en.wikipedia.org/wiki/Nash%E2%80%93Sutcliffe*model*efficiency_coefficient で確認できます。

1に近いほど良いです。

# 例

```@example
using PlantSimEngine

obs = [1.0, 2.0, 3.0]
sim = [1.1, 2.1, 3.1]

EF(obs, sim)
```
