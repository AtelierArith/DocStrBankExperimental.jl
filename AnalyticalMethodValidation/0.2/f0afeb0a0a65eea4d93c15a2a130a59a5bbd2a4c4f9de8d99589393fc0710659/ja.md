```
qc_report(at::AnalysisTable;
            id = r"PooledQC", 
            type = :estimated_concentration, 
            pct = true,
            stats = [mean, std, pct ? rsd_pct : rsd], 
            names = ["Mean", "Standard Deviation", "Relative Standard Deviation" * (pct ? "(%)" : "")], 
            colanalyte = :Analyte,
            colstats = :Stats
        )
```

QCデータの統計を計算します。

# 引数

  * `at`: `AnalysisTable`。
  * `id`: QCサンプルのための`Regex`識別子。
  * `pct`: 比率データをパーセンテージ (*100) に変換するかどうか。
  * `type`: 計算のためのデータタイプ。
  * `stats`: 統計関数。
  * `names`: 統計の名前。`nothing`が与えられた場合、`stats`が`names`として提供されます。
  * `colanalyte`: 分析物の列名。
  * `colstats`: 統計の列名。
