```
ap_report(at::AnalysisTable; 
            id = r"Pre.*_(.*)_.*", 
            type = :accuracy, 
            pct = true, 
            colanalyte = :Analyte,
            colstats = :Stats,
            colday = :Day,
            collevel = :Level
        )
```

精度と精密度を計算します。`NamedTuple`が返され、2つの要素があります：`daily`は各日の精度と標準偏差を含む`DataFrame`であり、`summary`は全体の精度、再現性、および再現性を含む`DataFrame`です。

# 引数

  * `at`: `AnalysisTable`。
  * `id`: AP実験サンプルのための`Regex`識別子。日付と濃度レベルが識別子にキャプチャされ、順序は`order`で設定できます。
  * `order`: `id`からキャプチャされた値の順序を設定するための文字列；Dは日付；Lは濃度レベルです。
  * `type`: 計算のためのデータタイプ。
  * `pct`: 比率データをパーセンテージ（*100）に変換するかどうか。
  * `colanalyte`: 分析物の列名。
  * `colstats`: 統計の列名。
  * `colday`: 検証日の列名。
  * `collevel`: レベルの列名。
