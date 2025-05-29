```
img = draw!(img, [drawable], [color])
img = draw!(img, [drawable] ,color)
img = draw!(img, [drawable])
```

`[drawable]`内のすべてのオブジェクトを、指定された順序で`img`に描画し、対応する色は`[color]`から取得されます。`[color]`はデフォルトで`oneunit(eltype(img))`になります。もし単一の色`color`のみが指定された場合、すべてのオブジェクトはその色で塗られます。
