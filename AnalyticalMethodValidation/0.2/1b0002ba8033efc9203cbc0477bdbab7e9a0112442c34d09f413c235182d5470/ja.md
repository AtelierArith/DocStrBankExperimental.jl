```
stability_report(at::AnalysisTable; 
                    day0 = r"S.*_(.*)_.*", 
                    stored = r"S.*_(.*)_(.*)_(.*)_.*", 
                    order = "CDL", 
                    type = :accuracy, 
                    pct = true,                             
                    colanalyte = :Analyte,
                    colstats = :Stats,
                    colcondition = :Condition,
                    colday = :Day,
                    collevel = :Level,
                    isaccuracy = true
                )
```

安定性を計算します。`NamedTuple`が返され、3つの要素が含まれます：`day0`はday0サンプルを含む`DataFrame`、`stored`は保存されたサンプルを含む`DataFrame`、`stored_over_day0`は`stored`を`day0`で割ったものです。

もし`day0`が利用できない場合、`day0`と`stored_over_day0`は空の`DataFrame`になります。

# 引数

  * `at`: `AnalysisTable`。
  * `day0`: day0サンプルのための`Regex`識別子。濃度レベルは識別子にキャプチャされます。
  * `stored`: 保存されたサンプルのための`Regex`識別子。保存条件、濃度レベル、保存日数が識別子にキャプチャされます；順序は`order`で設定できます。
  * `order`: `id`からキャプチャされた値の順序を設定するための文字列；Cは保存条件、Dは保存日数、Lは濃度レベルです。
  * `type`: 計算のためのデータ型。
  * `pct`: 比率データをパーセンテージ(*100)に変換するかどうか。
  * `colanalyte`: 分析物の列名。
  * `colstats`: 統計の列名。
  * `colcondition`: 保存条件の列名。
  * `colday`: 検証日の列名。
  * `collevel`: レベルの列名。
  * `isaccuracy`: 入力データが精度であるかどうか。
