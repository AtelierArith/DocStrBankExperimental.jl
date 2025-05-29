```
read_fits_image(filename::String)
```

FITSファイルを読み込み、画像、mappingParameters、およびスナップショット番号を返します。

# 返り値

  * image: 画像ピクセルを持つ2D配列
  * par:   画像に使用されるmappingParameters
  * snap:  マッピングされたスナップショットの番号
  * units: 画像の単位文字列

# 例

image, par, snap*nr, unit*string = read*fits*image(filename)
