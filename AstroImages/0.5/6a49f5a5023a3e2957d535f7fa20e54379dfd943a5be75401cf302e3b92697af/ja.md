```
recenter(img::AstroImage)
recenter(img::AstroImage, newcentx, newcenty, ...)
```

AstroImageの次元を`newcentx`などで指定されたピクセル位置に中心を合わせるように調整します。これは基礎となる配列には影響を与えず、AstroImageに関連付けられた次元を更新するだけです。`newcent`引数が提供されない場合は、すべての次元で画像を中央のピクセル（または分数ピクセル）に中心を合わせます。

例:

```julia
a = AstroImage(randn(11,11))
a[1,1] # 左下
a[At(1),At(1)] # 左下
r = recenter(a, 6, 6)
r[1,1] # まだ左下
r[At(1),At(1)] # 中央ピクセル
```
