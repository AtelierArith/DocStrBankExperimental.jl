```
read_allsky_fits_image(filename::String)
```

全空の画像を含むFITSファイルを読み込み、画像、スナップショット番号、および単位を返します。

# 返り値

  * image: 画像ピクセルを持つ2D配列
  * snap: マッピングされたスナップショットの番号
  * units: 画像の単位文字列

# 例

image, snap*nr, unit*string = read*allsky*fits_image(filename)
