Nx3のRGB値の配列を色空間からNx3のCIELAB値の配列に変換するための便利な関数です。この関数は、3チャンネルのRGB画像を3チャンネルのCIELAB画像に変換するためにも使用できます。

Colors.convert()関数は、デフォルトの白色点D65を使用しているようです。

```
 使用法:  lab = srgb2lab(rgb)

 引数:    rgb - N x 3のRGB値の配列または3チャンネルのRGB画像。
 戻り値:   lab - 3チャンネルのCIELAB画像のN x 3のLab値の配列。

```

関連情報: lab2srgb
