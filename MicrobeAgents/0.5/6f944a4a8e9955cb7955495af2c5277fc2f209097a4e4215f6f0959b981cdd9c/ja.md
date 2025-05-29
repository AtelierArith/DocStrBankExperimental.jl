```
AbstractChemoattractant{D,T}
```

化学誘引物質のための抽象型。次元数（`D`）と数値型（`T`、通常は`Float64`）が必要です。

インターフェースは、`AgentBasedModel`に対して動作する4つのコア関数によって定義されます：

  * `chemoattractant`: 化学誘引物質オブジェクトを返します
  * `concentration`: 濃度場の関数を返します
  * `gradient`: 濃度勾配の関数を返します
  * `time_derivative`: 濃度の変化率の関数を返します
  * `chemoattractant_diffusivity`: 化学誘引物質の熱拡散率を返します
