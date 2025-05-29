```
gdaldem(dataset, method, options=String[]; dest="/vsimem/tmp", color=name|GMTcpt, kw...)
```

DEMを分析および視覚化するためのツール。

### パラメータ

  * `dataset` ソースデータセット。
  * `method` 適用する処理（"hillshade"、"slope"、"aspect"、"color-relief"、"TRI"、"TPI"、"Roughness"のいずれか）。
  * `options` オプションのリスト（ファイル名やオープンオプションを含む可能性があります）。受け入れられるオプションはgdaldemユーティリティのものです。

# キーワード引数

  * `color` カラーファイル（"color-relief"処理には必須、そうでない場合は空であるべきです）。`color`が単なるCPT名の場合、そこからCPTを計算し、入力グリッドを使用します。
  * `kw...` `method`がhillshadeのときのkeyword=value引数。

### 戻り値

GMTグリッドまたは画像、またはGDALデータセット（ファイルがディスクに書き込まれた場合は何も返しません）。
