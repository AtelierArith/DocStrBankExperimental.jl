```
viz_fit(SampleData; DistFit=[], cumulative=false)
```

サンプルデータをフィッティングされた確率密度関数（PDF）および累積密度関数（CDF）に対して視覚化します。

# 引数

  * `SampleData`: サンプルデータの配列。
  * `DistFit`（オプション）: フィットする分布タイプの配列。提供されない場合は、デフォルトで `[Normal, LogNormal, Uniform]` になります。
  * `cumulative`（オプション）: 結果を累積形式で返します。デフォルトは確率密度形式です。

# 戻り値

`SampleData` の密度にフィッティングされたPDF / CDFが重ねられたプロットオブジェクト。
