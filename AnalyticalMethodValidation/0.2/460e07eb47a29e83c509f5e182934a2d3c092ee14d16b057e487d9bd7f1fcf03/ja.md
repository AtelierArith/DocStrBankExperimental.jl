```
recovery_report(at::AnalysisTable; 
                pre = r"Pre.*_(.*)_.*", 
                post = r"Post.*_(.*)_.*", 
                type = :area, 
                pct = true, 
                colanalyte = :Analyte,
                colstats = :Stats,
                collevel = :Level
            )
```

回収を計算します。

# 引数

  * `at`: `AnalysisTable`。
  * `pre`: プレスパイクサンプルのための `Regex` 識別子。濃度レベルは識別子にキャプチャされます。
  * `post`: ポストスパイクサンプルのための `Regex` 識別子。濃度レベルは識別子にキャプチャされます。
  * `type`: 計算のデータタイプ。
  * `pct`: 比率データをパーセンテージ (*100) に変換するかどうか。
  * `colanalyte`: 分析物の列名。
  * `colstats`: 統計の列名。
  * `collevel`: レベルの列名。
