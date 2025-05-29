```
img = draw!(img, drawable, color)
img = draw!(img, drawable)
```

`drawable`を`img`に色`color`を使って描画します。`color`は`oneunit(eltype(img))`にデフォルト設定されています。
