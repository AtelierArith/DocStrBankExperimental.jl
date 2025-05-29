Nx3の配列のCIELAB値を持つカラーマップをNx3のRGB値の配列に変換するための便利な関数。関数は、3チャンネルのCIELAB画像を3チャンネルのRGB画像に変換するためにも使用できます。

Colors.convert()関数は、デフォルトのホワイトポイントとしてD65を使用しているようです。

```
 Usage:  rgb = srgb2lab(lab)

 Argument:   lab - A N x 3 array of CIELAB values of a 3 channel CIELAB image.
 Returns:    rgb - A N x 3 array of RGB values or a 3 channel RGB image.
```

参照: srgb2lab
