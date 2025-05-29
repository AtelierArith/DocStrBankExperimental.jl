```
pressure(u, eq::BloodFlowEquations1D)
```

動脈のコンプライアンスに基づいて状態ベクトルから圧力を計算します。

### パラメータ

  * `u`: 状態ベクトル。
  * `eq`: `BloodFlowEquations1D`のインスタンス。

### 戻り値

スカラーとしての圧力。
