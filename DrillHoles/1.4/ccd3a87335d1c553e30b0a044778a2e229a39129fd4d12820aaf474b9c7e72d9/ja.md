```
desurvey(collar, survey, intervals;
         step=:arc, indip=:auto, outdip=:down,
         inunit=u"m", outunit=inunit, len=nothing,
         geom=:point, radius=1.0u"m")
```

`collar`、`survey`、および `intervals` テーブルに基づいて掘削穴をデサーベイします。オプションで、`step` メソッド、入力傾斜角の慣習 `indip`、出力傾斜角の慣習 `outdip`、入力単位 `inunit`、および長さ単位の出力単位を指定できます。

オプション `len` は、指定された長さにサンプルを合成するために使用でき、オプション `geom` は各サンプルのジオメトリを指定するために使用できます。

`:cylinder` ジオメトリの場合、オプション `radius` を使用して各シリンダーの半径を指定できます。

## ステップメソッド

  * `:arc` - 球面弧ステップ
  * `:tan` - 単純接線ステップ

See https://help.seequent.com/Geo/2.1/en-GB/Content/drillholes/desurveying.htm

## 傾斜の慣習

### 入力傾斜角

  * `:auto` - 最も頻繁に出現する傾斜符号は下向き
  * `:down` - 正の傾斜は下向き
  * `:up`   - 正の傾斜は上向き

### 出力傾斜角

  * `:down` - 正の傾斜は下向き
  * `:up`   - 正の傾斜は上向き

## 出力ジオメトリ

  * `:cylinder` - シリンダーを持つ地理空間データ
  * `:point`    - ポイントを持つ地理空間データ
  * `:none`     - 通常の列を持つデータフレーム
