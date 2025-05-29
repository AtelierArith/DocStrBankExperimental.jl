```
inout = inbbox(x::Real, y::Real, bbox) -> Bool
```

点 `x,y` がバウンディングボックス内にあるかどうかを確認します。

  * `x, y`: 点の座標。
  * `bbox` は xmin, xmax, ymin, ymax を持つ4要素の配列（ベクトル、行列、またはタプル）です。

### 戻り値

バウンディングボックス内の点に対して `true` を、外部の点に対して `false` を返します。
