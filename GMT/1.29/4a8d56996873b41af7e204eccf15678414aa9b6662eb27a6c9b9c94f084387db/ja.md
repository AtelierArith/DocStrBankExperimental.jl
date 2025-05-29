```
gdalshade(filename; kwargs...)
```

GDALメソッドを使用して陰影付きの地形を作成します（色画像と陰影強度をブレンド）。

  * kwargsには、`gdaldem hillshade`に引き渡す引数のkeyword=valueが含まれます。

例:     I = gdalshade("hawaii_south.grd", C="faa.cpt", zfactor=4);

### 戻り値

GMT RGB画像 ```
