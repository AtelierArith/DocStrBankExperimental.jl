```
flux_nonconservative(u_ll, u_rr, orientation::Integer, eq::BloodFlowEquations1D)
```

モデルの非保守フラックスを計算し、圧力の不連続性を処理するために使用されます。

### パラメータ

  * `u_ll`: 左側の状態ベクトル。
  * `u_rr`: 右側の状態ベクトル。
  * `orientation::Integer`: オリエンテーションインデックス。
  * `eq`: `BloodFlowEquations1D`のインスタンス。

### 戻り値

非保守フラックスベクトル。
