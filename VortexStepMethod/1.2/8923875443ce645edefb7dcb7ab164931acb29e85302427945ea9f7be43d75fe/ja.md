```
Section(LE_point::PosVector, TE_point::PosVector, aero_model)
```

指定された先端点、後縁点、および空力モデルを持つ新しい翼セクションを作成します。

# 引数

  * `LE_point::PosVector`: 先端点の座標
  * `TE_point::PosVector`: 後縁点の座標
  * `aero_model::AeroModel`: 空力モデルのタイプ（例：INVISCID、POLAR_VECTORS）

# 戻り値

  * `Section`: 指定されたパラメータと空力データのない新しいセクション
