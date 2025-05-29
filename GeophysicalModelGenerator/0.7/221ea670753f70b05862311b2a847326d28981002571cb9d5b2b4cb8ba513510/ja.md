```
interpolate_datafields_2D(Original::GeoData, New::GeoData; Rotate=0.0, Translate=(0,0,0), Scale=(1.0,1.0,1.0))
```

2D GeoDataグリッド`New`上でデータフィールド`Original`を補間します。通常は水平面に使用されます。

注意: `Original`は直交座標を持っている必要があります。もしそうでない場合、例えば回転されているために、回転角度`Rotate`を指定する必要があります。
