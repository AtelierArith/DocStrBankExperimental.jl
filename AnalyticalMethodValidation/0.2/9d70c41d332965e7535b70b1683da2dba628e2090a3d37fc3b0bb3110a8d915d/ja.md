```
me_report(at::AnalysisTable; 
            matrix = r"Post.*_(.*)_.*", 
            stds = r"STD.*_(.*)_.*", 
            type = :area, 
            pct = true, 
            colanalyte = :Analyte,
            colstats = :Stats,
            collevel = :Level
        )
```

マトリックス効果を計算します。

# 引数

  * `at`: `AnalysisTable`。
  * `matrix`: マトリックスを持つサンプルのための `Regex` 識別子。濃度レベルは識別子にキャプチャされます。
  * `stds`: 標準溶液のための `Regex` 識別子。濃度レベルは識別子にキャプチャされます。
  * `type`: 計算のためのデータタイプ。
  * `pct`: 比率データをパーセンテージ (*100) に変換するかどうか。
  * `colanalyte`: 分析物の列名。
  * `colstats`: 統計の列名。
  * `collevel`: レベルの列名。
