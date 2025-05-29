```
placeimage(matrix::AbstractMatrix{UInt32}, pos=O;
    alpha=1, centered=false)
```

画像行列を位置 `pos` に不透明度/透明度 `alpha` で描画します。

キーワード `centered=true` を使用して、画像の中心をその位置に配置します。
