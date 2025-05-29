```
reproject(input_data, output_projection; shape_out = nothing, order = 1, hdu_in = 1, hdu_out = 1)
```

画像データを補間を使用して新しい投影に再投影します。

# 引数

  * `input_data`: 再投影される画像データ。               ImageHDU、FITSオブジェクト、FITSファイルの名前、または画像行列とWCSTransformのタプルであることができます。
  * `output_projection`: データが再投影されるフレーム。                      フレームはWCSTransformオブジェクト、ImageHDU、FITS、またはFITSファイルの名前から取得できます。
  * `shape_out`: 再投影後の画像の形状。
  * `order`: 補間の順序。          0: 最近傍          1: 線形          2: 二次
  * `hdu_in`: FITSまたはFITSファイルの名前を入力として与えるときにHDU番号を指定するために使用されます。
  * `hud_out:` FITSまたはFITSファイルの名前を出力投影として与えるときにHDU番号を指定するために使用されます。
