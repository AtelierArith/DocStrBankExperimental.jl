```
x_min, x_max, y_min, y_max, x_inc_or_z_min, y_inc_or_z_max = getregion(dataset; gridreg=false, sds=0, GMT=false)
```

ファイルまたはGMTgrid、GMTimage、GMTdataset、またはGDALデータセットの領域の範囲を照会します。

オプション`gridreg`と`sds`はGDALデータセット専用です。`input`が文字列（ファイル名）の場合、デフォルトはGDALを使用し、領域はデフォルトで「ピクセル登録」となります。`gridreg=true`を使用して「グリッド登録」を強制します。文字列としての`input`の場合、`GMT=true`を使用して結果を`grdinfo`によって提供されるように強制します。ファイル/オブジェクトを照会するためにGMTまたはGDALを使用する不幸な結果は、5番目と6番目の出力（`input`がGMTdatasetの場合は4つのみ）が異なる内容を持つことです。GDALで読み取るときは`x_inc, y_inc`になり、GMTで読み取るときは`z_min, z_max`になります。
