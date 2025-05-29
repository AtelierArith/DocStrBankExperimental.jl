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

Compute recovery.

# Arguments

  * `at`: `AnalysisTable`.
  * `pre`: `Regex` identifier for prespiked samples. The concentration level is captured in the identifier.
  * `post`: `Regex` identifier for postspiked samples. The concentration level is captured in the identifier.
  * `type`: data type for calculation.
  * `pct`: whether converting ratio data into percentage (*100).
  * `colanalyte`: column name of analytes.
  * `colstats`: column name of statistics.
  * `collevel`: column name of level.
