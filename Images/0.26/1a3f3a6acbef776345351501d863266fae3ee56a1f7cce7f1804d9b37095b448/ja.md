```
m = magnitude(grad_x, grad_y)
```

`grad_x` と `grad_y` で与えられた勾配画像の大きさを計算します。`sqrt(grad_x.^2 + grad_y.^2)` と同等です。

`grad_x` と `grad_y` と同じサイズの大きさ画像を返します。
