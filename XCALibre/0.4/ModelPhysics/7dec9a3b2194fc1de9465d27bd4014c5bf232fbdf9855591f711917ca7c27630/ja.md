```
SensibleEnthalpy <: AbstractEnergyModel
```

エネルギーモデル、係数、およびそれに関連するフィールドを表す型。

### フィールド

  * 'h'    – 感覚エンタルピー ScalarField。
  * 'T'    – 温度 ScalarField。
  * 'hf'   – 感覚エンタルピー FaceScalarField。
  * 'Tf'   – 温度 FaceScalarField。
  * 'K'    – 特定の運動エネルギー ScalarField。
  * 'dpdt' – 圧力の時間微分 ScalarField。
  * 'updated_BC' – 固定値境界で温度を感覚エンタルピーに変換する境界条件関数。
  * 'coeffs' – モデル係数のタプル。
