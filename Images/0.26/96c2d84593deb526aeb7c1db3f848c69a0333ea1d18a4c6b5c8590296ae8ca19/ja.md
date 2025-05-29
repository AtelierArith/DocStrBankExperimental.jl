```
orientation(grad_x, grad_y) -> orient
```

`grad_x` と `grad_y` から与えられた勾配画像の最も強いエッジの方向角を計算します。 `atan(grad_x, grad_y)` と同等です。 `grad_x` と `grad_y` の両方が実質的にゼロの場合、対応する角度はゼロに設定されます。
