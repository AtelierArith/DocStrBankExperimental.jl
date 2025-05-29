```
depthwiseconv(x, w; stride=1, pad=0, dilation=1, flipped=false)
```

フィルター `w` を用いた入力 `x` に対する深さ方向の畳み込み操作です。`x` と `w` はそれぞれ1d/2d/3d 畳み込みにおける3d/4d/5d テンソルです。
