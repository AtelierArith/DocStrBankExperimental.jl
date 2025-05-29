```
interpolate_datafields_2D(Original::CartData, New::CartData; Rotate=0.0, Translate=(0,0,0), Scale=(1.0,1.0,1.0))
```

データフィールド `Original` を 2D CartData グリッド `New` に補間します。通常は水平面に使用されます。

注意: `Original` は直交座標を持っている必要があります。もしそうでない場合、例えば回転されている場合は、回転された角度 `Rotate` を指定する必要があります。
