```
inverse_mnf(transformation::MNF, raster::AbstractRaster)
inverse_mnf(transformation::MNF, signatures::Matrix)
```

元の画像または署名を回復するために逆最小ノイズ分数（MNF）変換を実行します。

# パラメータ

  * `transformation`: 以前に適合されたMNF変換。
  * `raster`: 以前に変換された画像を表す`AbstractRaster`。バンドの数は元の画像のバンド数以下である必要があります。
  * `signatures`: 変換された署名のn x p行列で、nは署名の数、pは保持された成分の数です。
