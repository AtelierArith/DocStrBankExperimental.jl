```
friction(u, x, eq::BloodFlowEquations1D)
```

血流方程の摩擦項を計算します。これは動脈壁に沿った流れに対する粘性抵抗を表します。

### パラメータ

  * `u`: 断面積と流量を含む状態ベクトル。
  * `x`: 動脈に沿った位置。
  * `eq::BloodFlowEquations1D`: 血流モデルのインスタンス。

### 戻り値

スカラーとしての摩擦係数。
