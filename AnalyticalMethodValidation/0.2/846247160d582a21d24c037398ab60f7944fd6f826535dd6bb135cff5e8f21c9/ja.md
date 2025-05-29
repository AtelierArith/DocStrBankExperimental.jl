```
sample_report(at::AnalysisTable; id = r"Sample_(\d*).*", type = :estimated_concentration, colanalyte = :Analyte)
```

サンプルデータの平均を計算します。

# 引数

  * `at`: `AnalysisTable`。
  * `id`: QCサンプルのための`Regex`識別子。
  * `type`: 計算のためのデータタイプ。
  * `colanalyte`: 分析物の列名。
