```
flux_nonconservative(u_ll, u_rr, normal, eq::BloodFlowEquations2D)
```

2D血流モデルに基づいて、法線ベクトルに基づく非保守フラックスを計算します。

### パラメータ

  * `u_ll`: 左側の状態ベクトル。
  * `u_rr`: 右側の状態ベクトル。
  * `normal`: フラックスの方向を示す法線ベクトル。
  * `eq::BloodFlowEquations2D`: `BloodFlowEquations2D`のインスタンス。

### 戻り値

非保守フラックスベクトル。
