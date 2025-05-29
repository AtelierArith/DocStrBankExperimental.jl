```
phase(grad_x, grad_y) -> p
```

`grad_x` と `grad_y` によって与えられる勾配の回転角を計算します。`atan(-grad_y, grad_x)` と同等ですが、`grad_x` と `grad_y` の両方が実質的にゼロの場合、対応する角度はゼロに設定されます。
